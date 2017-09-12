# Deployment of Kylo on AWS with Vagrant

[Kylo](https://kylo.io/) an open source data lake is built on a heavy stack.
Running it locally requires a high-end buffed-up laptop. This Vagrant script
eases the deployment of the sandbox on AWS and makes easier to try it, extend
it, or contribute to it.

This will deploy [Kylo 0.8.3 based on cloudera sandbox](https://kylo.io/quickstart-ami.html).

## Requirements

You need:

* an [AWS account](https://aws.amazon.com/),
* [Vagrant](https://www.vagrantup.com/docs/installation/), and
* [Vagrant AWS plugin](https://github.com/mitchellh/vagrant-aws#usage).

### Credentials

In your AWS account:

* [create an IAM user](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)
  to which [you give the permission `AmazonEC2FullAccess`](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html),
* write down the key and the secret,
* [create a SSH key in EC2 and store the private key](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html), and
* [enable full access to the machine from your IP address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html).

With those, you can create the following environment variables:

```Bash
export AWS_KEY="your key"
export AWS_SECRET="your secret"
export AWS_KEYNAME="your ssh key name"
export AWS_KEYPATH="the path to your ssh private key"
```

### Vagrant AWS Plugin and dummy box

You need to install the Vagrant AWS plugin first.

```Bash
vagrant plugin install vagrant-aws
```

Then, you need a dummy Vagrant box.

```Bash
vagrant box add aws-dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
```

## Usage

You can deploy the Kylo sandbox with:

```Bash
vagrant up
```

When deployed you can:

* ssh into it with `vagrant ssh`,
* browse the public hostname of your box (the login and password being `dladmin` and `thinkbig` respectively).

To stop your instance, do:

```Bash
vagrant halt
```

## License

This project is licensed under the terms of the [MIT license](LICENSE.md).

## Contributors

* [toch](https://github.com/toch)
