# Linux OS Security Users and Groups

We want to create two new accounts on the system, for users Alice and Bob. We also want to create some new groups for these users.

Note: usernames in Linux are case sensitive. "Alice" is not the same as "alice". It is not usual to create users with uppercase in the names so we want user accounts called "alice" and "bob".


Create a new group using the YaST GUI; call it cnsm2.

Use the YaST GUI to add alice with the required group settings etc. (see below).

Create a user account for bob using useradd.

Modify it using usermod to the settings below (you can also use options to useradd when you create the account).

Change the password for the new bob account using passwd(1).


REQUIRED SETTINGS:

Each user should be in their own group, e.g. alice should be in group alice as the primary group, and the gid of group alice should be the same as alice's uid. This is a common convention for setting up user accounts (called user private groups; not the default bahaviour on SuSE Linux, but used for example by Red Hat Linux). The user private group should be the user's primary group.

In addition, alice and bob should be in cnsm2.

 alice and bob must not be in the users group.

You will need to remember the passwords for all these accounts, so either set them to the usual password on the VM (cnsm2vm) or write them down somewhere!



TO DO

Capture screenshots of the GUI showing the alice and bob accounts when you have created them.

Look at the /etc/passwd and /etc/group files showing the new entries.

In the quiz (link below), upload the requested information about the accounts and the commands used (follow the questions as you work through the tasks).



## Question 1

Upload a screenshot of the GUI showing the new cnsm2 group.

## Answer 1

## Question 2

Upload a screenshot showing the new alice account being created in the GUI.

## Answer 2

## Question 3

Paste in here the command line session in which you create and modify an account "bob" using `useradd` and `usermod`. Be sure you use the correct options to the commands to get the right settings.

Also show here the command where you change the password on the new account.

## Answer 3

```bash
sudo groupadd bob
sudo useradd --create-home --home-dir /home/bob --shell /bin/bash --gid bob --groups cnsm2 bob
sudo passwd bob
```

```out

```

## Question 4

Upload a screenshot showing the two new accounts created in the GUI.

## Answer 4


## Question 5

Upload the /etc/passwd file here showing the new accounts.

You may make a comment if you wish

## Answer 5

## Question 6

Upload the /etc/group file here showing the new groups.

You may make a comment if you wish.

## Answer 6