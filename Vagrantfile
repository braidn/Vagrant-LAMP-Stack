require 'berkshelf/vagrant'

Vagrant.configure('2') do |config|
  # Define VM box to use
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  # Use hostonly network with a static IP Address
  config.vm.network :private_network, ip: "172.90.90.80"

  # Set share folder
  config.vm.synced_folder ".", "/home/vagrant/shared", :nfs => true

	config.berkshelf.enabled = true
  # Enable and configure chef solo
  config.vm.provision :chef_solo do |chef|
		chef.add_recipe "apt"
		chef.add_recipe "build-essential"
		chef.add_recipe "openssh"
		chef.add_recipe "postfix"
		chef.add_recipe "openssl"
		chef.add_recipe "apache2"
		chef.add_recipe "apache2::mod_php5"
		chef.add_recipe "apache2::mod_rewrite"
		chef.add_recipe "apache2::mod_ssl"
		chef.add_recipe "mysql"
		chef.add_recipe "mysql::server"
		chef.add_recipe "memcached"
		chef.add_recipe "misc::packages"
		chef.add_recipe "misc::vhost"
		chef.add_recipe "misc::db"
		chef.add_recipe "chef-dotdeb"
		chef.add_recipe "chef-dotdeb::php54"
		chef.add_recipe "rvm::system"
		chef.add_recipe "readline"
		chef.add_recipe "perl"
		chef.add_recipe "xml"
		chef.add_recipe "zlib"
		chef.add_recipe "nodejs::npm"
		chef.add_recipe "php"
    chef.json = {
      :misc => {
        # Project name
        :name           => "server",

        # Name of MySQL database that should be created
        :db_name        => "dbname",

        # Optional database dump to be imported when server is provisioned
        # If the file doesn't exist, it is just ignored
        :db_dump        => "/home/vagrant/shared/dump.sql",

        # Server name and alias(es) for Apache vhost
        :server_name    => "server.dev",
        :server_aliases => "*.server.dev",

        # Document root for Apache vhost
        :docroot        => "/home/vagrant/shared/public_html",
      },
      :mysql => {
        :server_root_password   => 'root',
        :server_repl_password   => 'root',
        :server_debian_password => 'root',
        :bind_address           => '172.90.90.80',
        :allow_remote_root      => true
      },
			:rvm => {
				:rubies => [ "1.9.3-p286"  ],
				:default_ruby => '1.9.3',
				:group_users => ["vagrant"],
				:global_gems => [
					{ :name => 'bundler' },
					{ :name => 'rake' },
					{ :name => 'chef' },
					{ :name => 'passenger' }
				]

			}
    }
  end
end
