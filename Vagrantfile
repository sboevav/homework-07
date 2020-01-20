# -*- mode: ruby -*-
# vim: set ft=ruby :
# -*- mode: ruby -*-
# vim: set ft=ruby :

MACHINES = {
  :centos => {
        :box_name => "centos/7",
        :ip_addr => '192.168.11.101'
  }
}

Vagrant.configure("2") do |config|

  MACHINES.each do |boxname, boxconfig|

      config.vm.define boxname do |box|

          box.vm.box = boxconfig[:box_name]
          box.vm.host_name = boxname.to_s

          #box.vm.network "forwarded_port", guest: 3260, host: 3260+offset

          box.vm.network "private_network", ip: boxconfig[:ip_addr]

          box.vm.provider :virtualbox do |vb|
            vb.customize ["modifyvm", :id, "--memory", "256"]
          end

          
	  $script = <<-SCRIPT
           sudo mkdir -p ~root/.ssh
           sudo cp ~vagrant/.ssh/auth* ~root/.ssh

	   sudo yum install -y redhat-lsb-core
           sudo yum install epel-release -y -q
           sudo yum install fish wget -y -q
# Install tools for building rpm
           sudo yum install rpmdevtools rpm-build -y -q
           sudo yum install tree yum-utils mc wget gcc vim git -y -q
# Install tools for building woth mock and make prepares    
           sudo yum install mock -y -q
           sudo usermod -a -G mock root
# Install tools for creating your own REPO
           sudo yum install nginx -y -q
           sudo yum install createrepo -y -q
# Install docker-ce
           sudo yum install -y -q yum-utils links \
#           device-mapper-persistent-data \
#           lvm2
#           sudo yum-config-manager \
#           --add-repo \
#           https://download.docker.com/linux/centos/docker-ce.repo
#           yum install docker-ce docker-compose -y -q
#           systemctl start docker
#           docker run hello-world

# main homework
		wget https://nginx.org/packages/centos/7/SRPMS/nginx-1.14.1-1.el7_4.ngx.src.rpm
		rpm -i nginx-1.14.1-1.el7_4.ngx.src.rpm
		mkdir rpmbuild/BUILD
		mkdir rpmbuild/BUILDROOT
		mkdir rpmbuild/RPMS
		mkdir rpmbuild/SRPMS
		wget https://www.openssl.org/source/latest.tar.gz
		tar -xvf latest.tar.gz
		sudo rm rpmbuild/SPECS/nginx.spec
		sudo cp /vagrant/nginx.spec rpmbuild/SPECS/
		sudo yum-builddep -y rpmbuild/SPECS/nginx.spec
		rpmbuild -bb rpmbuild/SPECS/nginx.spec
		sudo yum remove nginx -y
		sudo yum localinstall -y rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm
		sudo systemctl start nginx
		sudo mkdir /usr/share/nginx/html/repo
		sudo cp rpmbuild/RPMS/x86_64/nginx-1.14.1-1.el7_4.ngx.x86_64.rpm /usr/share/nginx/html/repo/
		sudo wget https://www.percona.com/downloads/percona-release/redhat/LATEST/ -O /usr/share/nginx/html/repo/percona-release-latest.noarch.rpm
		sudo createrepo /usr/share/nginx/html/repo/
		sudo rm /etc/nginx/conf.d/default.conf
		sudo cp /vagrant/default.conf /etc/nginx/conf.d/
		sudo nginx -s reload
		sudo cp /vagrant/otus.repo /etc/yum.repos.d/
		sudo yum install percona-release -y


	  SCRIPT
	  box.vm.provision "shell", inline: $script, privileged: false

      end
  end
end
