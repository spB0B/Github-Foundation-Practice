## Cloning

We can clone using three ways

First of all I am going to create a tmp directory to see the function of the ```git clone``` command

```sh
mkdir /workspaces/tmp && cd tmp
```

### HTTPS
```sh
git clone https://github.com/spB0B/Github-Foundation-Practice.git
```
>may need a FGT to push commit from a local workspace if you haven't signed into the GitHub from that workspace

go to settings > developer option

### SSH
```ssh
git@github.com:spB0B/Github-Foundation-Practice.git
```
> you may need to create a ssh key first in order to clone the repository

### GitHub CLI

When using the GitHub CLI we forst have to install it. In my case I had to use Homebrew to install it using `homebrew install gh`. After installing you can check whether it is installed using the command `gh --version`
```sh
homebrew install gh
```

then you have to frist login to the CLI
```sh
gh auth login
```
I tried to do something before loging in but it just prompt to login. After logi we can do so much things we can try `gh` to see what we can do. the terminal prompts us to chose options:
> GitHub.com > SSH > "public key" > title for the pub key > login with web browser

I chose this order. but I tried to chose authentication token, it didn't work. This way CLI automatically creates a SSH key in out account and prompts us a web browser to authentication.

after authentication we can use CLI to clone the repo using:
```sh
gh repo clone spB0B/Github-Foundation-Practice
```

## Git Hidden folder

There is a hidden folder inside that cloned repository called `.git`. It has things like `HEAD, config, description, hooks, index, info, logs, objects, packed-refs, refs`. some of the things are encoded but some files has important things like url of this repo.

To create new repo I created /workspaces/tmp2. then command `git init` to initiate a git repository.

after creating the `Readme.md` inside the tmp2, I `git status` to `check the status of the repo`. there I could see files that are currently not tracked by the git. So I used `git add` which is used to `add everything that is not being tracked`. and we can use the file name instead of the period that way git only stage that one.  

## Commits

git commit is used to commit the changes to the repository.
```sh
git commit -m 'message'
```
the `-m` flag gives the commit message from the terminal. that way we don't have to type the commit message in the editor. the message is also useful because I think it is used to reverse commits.

## Branches

Branches are used as a path of development. we can create a branch using
```sh
git branch "branch-name"
```
then we can see available branches using 
```sh
git branch
```
we will use branches to add a new feature or separate someones work from main branch.We also can change branches 
```sh
git checkout "branch-name"
```
after chaning the brnach we can commit and push changes to that branch
```sh
git push --set-upstream origin dev
```
 after this there will be a new branch of the main that hass all the content of the main branch and some extra files that are not in the main branch.
## Remotes

## Stashing

## Mergings

## Push

this is me trying to push the the changes after cloning the repository to my local workspace. first I cloned the repo using `git clone` and then now I am trying to do `git push` from this local env. 

### FGT -Fine Grained Token

FGT is a one time appearing token that allows us to use instead of the password. we can set permissions, valid time period for FGT. nothing will cache that value.

### GitHub SSH keys

In settings > SSH and GPG keys you can add a SSH key. then only you can clone a repository using ssh,which is the most convinent way of doing it because it doesn't need every time password when we clone the repo.
#### steps
1. In your local workspace terminal create the key using
```sh
ssh-keygen -t ed25519/rsa -C "email in your github account"
```
>In this step you can either use ECC or RSA. here ECC is used.
>you can choose a location and a passphase as you prefer which can imporve the security of your key.
2.Then tou have to start the SSH agent and add the key
```sh
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```
this loads the private key to memory so you don't have to use that evey time you use that to get into github. Finally if you don't want caching the key you can modify the file `~/.ssh/config` or use the private key directly to access the git `ssh -i ~/.ssh/id_ed22519 "github ssh link"`

>~/.ssh/id_ed25519 can be changed. if you have changed the location of the key in step 1. so use the proper location here
3. Copy the public key
```sh
pbcopy < ~/.ssh/id_ed25519.pb
```
Copy the public key and paste it in the key section of the GitHub. Now you can clone the repo using the command `ssh git@github.com:spB0B/Github-Foundation-Practice.git`.
