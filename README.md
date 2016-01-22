# ansible-slack-notify-ssh

Ansible role for posting successful SSH logins to Slack.

Based on [this blog post by Sandrino Di Mattia](http://sandrinodimattia.net/posting-successful-ssh-logins-to-slack/).

## Installation

Set up a Slack webhook (detailed in the blog post if you don't know how).

```
$ ansible-galaxy install https://github.com/duggan/ansible-slack-notify-ssh
```

## Usage

Create a task like:

`slack-notify-ssh.yml`

```yml
---
- name: Configure Slack SSH login notifications
  vars:
    hosts: all
  hosts: "{{ hosts }}"
  sudo: yes
  roles:
    - role: ansible-slack-notify-ssh
      slack_notify_ssh_webhook_url: https://hooks.slack.com/services/foo/bar/baz
      slack_notify_ssh_channel: "#infrastructure"
```

Run, and test it out!

To remove:

```
- name: Remove Slack SSH login notifications
  vars:
    hosts: all
  hosts: "{{ hosts }}"
  sudo: yes
  roles:
    - role: ansible-slack-notify-ssh
      slack_notify_ssh_state: absent
```
