- Generate ssh key

```shell
ssh-keygen -t ed25519 -C "asullivan219@pm.com"
```

- Will ask for a folder to place the key
	- default is at `~/.ssh/`
- Will ask for a passphrase


Add to ssh-agent

```bash
eval "$(ssh-agent -s)"
```

add key to agent:

```bash
ssh-add ~/.ssh/id_ed25519
```

- If you changed the name of the key then you may need to alter the command
- make sure toc check you dont already have a key with the same name

Now that the key is on your ssh agent, we need to add the public key to github

Copy the results of this command to your cliopboard
```bash 
cat ~/.ssh/id_ed25519.pub

```

on Github go to settings > access > ssh and gpg keys

past the key into the field for ssh keys.