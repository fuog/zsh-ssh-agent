# Ssh-agent

> Ssh-agent management for zsh, with additional feature for unlocking private-keys


## Install

1. Either…
  - Clone this repo
  - add it as a submodule, or
  - just download `ssh-agent.zsh`

2. Source `ssh-agent.zsh` in your '.zshrc'


3. (optional)

   - create `unlock_ids` file in the `$HOME/.ssh/unlock_ids`
   - see the [example file](unlock_ids.template) on how to write it

This will look for a matching entry within the `unlock_ids` file and
will use the corresponding command to unlock the private key.

> NOTE: Bare in mind the security risk that comes with this plugin-feature!

## Integration
### [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
Symlink (or copy) `snooch.zsh` to `~/.oh-my-zsh/custom/ssh-agent.zsh`.

### [antigen](https://github.com/zsh-users/antigen)
Update your `.zshrc` file with the following line:

```sh
antigen bundle bobsoppe/zsh-ssh-agent
```

### [antibody](https://github.com/getantibody/antibody)
Update your `.zshrc` file with the following line:

```sh
antibody bundle bobsoppe/zsh-ssh-agent
```

### [zplug](https://github.com/zplug/zplug)
Update your `.zshrc` file with the following line:

```sh
zplug bobsoppe/zsh-ssh-agent, use:ssh-agent.zsh, from:github
```

## troubleshooting

If you run into problems with the ssh-agent not working as expected, you may have some other ssh-agent that is messing up your shell configuration. 

- i did run in to the gnome-keyring-ssh-agent. See [this page on how to disable](https://wiki.gnome.org/Projects/GnomeKeyring/Ssh) this feature of gnome.
- i did also run in to a problem with [Xsessions starting a ssh-agent](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=658124). You would have to [remove or comment](https://manpages.ubuntu.com/manpages/focal/en/man5/Xsession.options.5.html) the `use-ssh-agent` flag in `sudo vi /etc/X11/Xsession.options` to stop that beavior. Note: this is system level for all users.
