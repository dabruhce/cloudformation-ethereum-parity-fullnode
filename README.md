


````text
 ./parity --chain ropsten --jsonrpc-hosts all --jsonrpc-interface all --jsonrpc-apis all --snapshot-peers=25 --max-peers=10 --min-peers=25
````

````text
#base deploy commands for amzlinux
sudo bash && cd ~
yum -y update
yum install -y git make gcc-c++ gcc file binutils openssl-devel libudev-devel
curl -sSf https://static.rust-lang.org/rustup.sh -o rustup.sh
export HOME=~
sh rustup.sh --disable-sudo
export PATH="$PATH:/usr/local/bin"
git clone https://github.com/paritytech/parity
cd parity
git checkout b49c44a1982bfac03f70641cd570560878b83658
cargo build --release
cp ./target/release/parity /usr/local/bin/
parity --chain ropsten --jsonrpc-hosts all --jsonrpc-interface all --snapshot-peers=25 --max-peers=10 --min-peers=25
````

````text
On t2.medium its takes roughly 45 minutes before blockchain begins syncing, this can be cut out with a built ami
blockchain sync takes about 25 minutes
total time ~ 1:15

benchmark manual steps w/ m3.large takes & Iops: "3000", 15mins build, 7 mins sync
````

````text
create ami to speed up deployment: https://aws.amazon.com/blogs/devops/how-to-create-an-ami-builder-with-aws-codebuild-and-hashicorp-packer/
add SSL
add DNS
change health check to be 443:8545
allow entry of commitId
add scaling
Add cf logs: https://aws.amazon.com/blogs/devops/view-cloudformation-logs-in-the-console/
some sort of run manager
add ethstats?
````
