Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu-server-1310-x64-virtualbox"
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/ubuntu-1310-x64-virtualbox-puppet.box"

  config.vm.provision "shell", inline: <<-EOS
    apt-get -qq update
    apt-get install -y git ruby-dev build-essential libxml2-dev libxslt1-dev
    gem install --no-ri --no-rdoc librarian-puppet bundler
    mkdir -p /usr/share/puppet/modules
    [ ! -e /usr/share/puppet/modules/arcanist ] && ln -s /vagrant /usr/share/puppet/modules/arcanist
    (cd /usr/share/puppet/modules/arcanist && librarian-puppet install --path /usr/share/puppet/modules)
    (cd /vagrant && bundle)
    touch /etc/puppet/hiera.yaml
  EOS
end
