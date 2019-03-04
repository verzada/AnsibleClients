Following this youtube clip:
https://www.youtube.com/watch?v=FEdXUv02Dbg

Firewall settings for VirtuaBox:
https://serverfault.com/questions/225155/virtualbox-how-to-set-up-networking-so-both-host-and-guest-can-access-internet

Host side:
First set powershell execution policy as admin:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
then
run the ansible script (see link below) as admin
To easily copy it, choose to see the RAW file
https://github.com/ansible/ansible/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1

Ansible side:

sudo pip install pywinrm
update hosts file with ip's or hostnames 
ansible dev -i hosts -m win_ping -vvvv

Output:
/mnt/d/Github/AnsibleClients$ ansible dev -i hosts -m win_ping -vvvv
192.168.56.101 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}

Possible issues if the ping is not successfull:
Check if it's possible to do a normal 'ping' the host and server from eachother.
If the ping isn't successfull, it's most likely a firewall issue where both the ansible server and host must be configured to allow traffic between them.

run 
ansible-playbook -i hosts choco.yaml -vvv
or
ansible-playbook -i hosts choco.yaml -vvvv
