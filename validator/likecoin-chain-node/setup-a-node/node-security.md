# Node Security

Below are general guidelines for reducing attack vectors over network:

* Ensure unattended upgrades are enabled
* Block all ports except required ones
  * Setup firewall via `ufw` or `iptables`
  * Optionally for cloud host, block ports via security group instead
* SSH Port should be open to trusted IP addresses only
* SSH login with password should be disabled, authenticate with a `ed25519` key instead
  * For extra security, use a yubikey with `ed25519-sk` resident key

The exact steps are out of scope of this guide, please refer to other online sources or consult the community discord. Below are some good 3rd party guides for reference:

* [UFW usage](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-20-04)
* [Generate ed25519 SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
* [Deploy SSH key to server](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server#step-2-copying-an-ssh-public-key-to-your-server)
* [SSH Hardening](https://www.digitalocean.com/community/tutorials/how-to-harden-openssh-client-on-ubuntu-20-04)

The physical security of the host should be reviewed as well.

For validators, we encourage the use [tmkms](https://docs.osmosis.zone/developing/keys/tmkms.html) for improved signing security
