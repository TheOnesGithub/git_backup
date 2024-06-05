# git backup is the 80/20 of backing up your repositories

## The problem
Ephemeral workspaces are a good idea. Even if its on my local computer. 
What happens of the homeless guy mugs me on my way to sarbucks to work and takes my takes my sticker holder?
I want the set up to be easy and fast.
How ever that means I ofter only have one copy of my repositories. Github.

* microsoft buys github and shuts it down. (just kidding its not google)
* github gets ddosed again
* a soler flare destroys my data
* the data center github is storing data in gits hit with container ship that lost power

## The Goal
3 2 1 or better 3 copys of your repositories in 2 diffrent places and 1 of them is off site.

## What is it
git backup is a docker compose file that runs a gitea server. You use it to mirror repos and all the data is stored in a volume on the host machine. 
This way you have two copys of the repositories remote server you are mirroring (github?) and one on your local machine. 
You can then backup the volume to a cloud service or a usb drive. 
You can then restore the repositories by copying the backed up volume to any host and running git backup.
Now you have a copy of your repositories in three diffrent places and two are remote.

## How to use
1. clone the repository
2. run the docker compose file
3. go to localhost:4500
4. set the options (if first time)
5. login with gitea and the email and password (assuming you left the default values)
6. click on the create button in the top right and chouse mirror
7. repeat setp 6 for all the repositories you want to backup
8. your repositories are now saved on your host machine in the ~/.gitea folder 
9. how you have two copys of your repositories one on your remote server (github?) and one on your local machine
10. backup the ~/.gitea folder to a cloud service or a usb drive
11. if you ever need to restore your repositories just copy the ~/.gitea folder back to your host machine and run the docker compose file again

## setup
```bash
git clone https://github.com/TheOnesGithub/git_backup.git
docker compose up -d
```
to stop it 
```bash
docker compose down
```

