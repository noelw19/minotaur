
add to .bash_profile
export PATH=$PATH:~/path/to/minotaur/

-tag will find all boxes in config with that tag and copy to or ssh to


Copy files to all boxes marked with tag
minotaur -c -f ./path/to/fileOrDir -t tag

SSH to boxes with tag
minotaur -s -t tag

SSH to boxes with tag in specific environment
minotaur -s -t tag -e dev

Show current environment config
minotaur -p

Don't show tmux help
minotaur -z


Environment Config files

dev = conf-dev.json
pre = conf-pre.json
prod = conf-prod.json

Simple config setup 

{
    "sshKey": "~/.ssh/user_ssh_key",
    "username": "noel.williams",
    //boxes include each server name, an ip and a tag
    //if a username is present within the individual box this will overide the default username set above
    "boxes": {
        "JF1": {
            "ip":"10.0.4.10",
            "tag": "jf",
            "username": "noel.williams",
        },
        "JF2": {
            "ip":"10.0.4.11",
            "tag": "jf" 
        }
    }
}