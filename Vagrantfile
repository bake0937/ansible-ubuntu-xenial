Vagrant.configure("2") do |config|
  config.vm.define "ubuntu-xenial64" do |web|
    web.vm.box = 'ubuntu/xenial64'
    web.vm.hostname = 'ubuntu-xenial64'
    web.vm.network :private_network, ip: '192.168.50.102'

    web.vm.provider :virtualbox do |vb|
      vb.name = "ubuntu-xenial64"
      vb.gui = false
      vb.cpus = 4
      vb.memory = 4096
      vb.customize ['modifyvm', :id, '--natdnsproxy1', 'off']
      vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'off']
    end

    web.disksize.size = '40GB'
    web.mutagen.orchestrate = true

    # 現在のディレクトリにプロジェクトフォルダを置いていれてばローカル開発環境内でも操作が可能になる
    web.vm.synced_folder './', '/home/vagrant/projects', type: "rsync",
      rsync_auto: true,
      rsync__exclude: ['node_modules/', 'log/', 'tmp/']

    web.vm.provision :docker, run: 'always'
    web.vm.provision :docker_compose

    web.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible-ubuntu-xenial/site.yml"
      ansible.inventory_path = "ansible-ubuntu-xenial/hosts"
      ansible.limit = 'all'
    end
  end
end
