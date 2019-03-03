Following this youtube clip:
https://www.youtube.com/watch?v=FEdXUv02Dbg

Host side:
Run this powershell script on the host
To easily copy it, choose to see the RAW file
https://github.com/ansible/ansible/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1



ansible side:

sudo pip install pywinrm
update hosts file
ansible dev -i hosts -m win_ping

Output:
/mnt/d/Github/AnsibleClients$ ansible dev -i hosts -m win_ping
192.168.56.101 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}

run 
ansible-playbook -i hosts choco.yaml