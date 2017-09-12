require "vagrant-aws"

Vagrant.configure("2") do |config|
  config.vm.box = "aws-dummy"

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = ENV["AWS_KEY"]
    aws.secret_access_key = ENV["AWS_SECRET"]

    # kylo-cloudera-sandbox-0.8.3
    aws.ami = "ami-befd50d1"
    aws.instance_type = "m4.2xlarge"
    aws.region = "eu-central-1"

    override.ssh.username = "centos"
    aws.keypair_name = ENV["AWS_KEYNAME"]
    override.ssh.private_key_path = ENV["AWS_KEYPATH"]
  end
end
