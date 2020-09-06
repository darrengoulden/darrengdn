---
layout: post
title:  "Host your own alternate dialling instruction page"
date:   2020-09-04 08:00:00 +0100
categories: pexip cvi
comments: true
---

When you enable Microsoft Teams integration with Pexip Infinity one of the [final steps](https://docs.pexip.com/admin/teams_connector.htm#authorize_lobby){: .acustom } is to configure the dialling instructions for your users using the `SkypeOnlineConnector` PowerShell module.  The dialling instructions are embedded into a Microsoft Teams invite and enables users to visit a webpage with additional joining instructions for the meeting.

![cvi-invitation-instructions]({{ site.baseurl }}/assets/img/2020-09-04-hosting-your-own-alternate-dialling-instructions/invitation_instructions_784x602.png){: .center-image }

Pexip Infinity nodes host a default page for these dialling instructions, and this is where you would normally point your users but this default template does not suit everyone (and it is also not supported to edit this default template directly on the Pexip nodes), if you would like to modify this and host your own dialling instructions, follow the steps below.

![pexip-default-cvi-page]({{ site.baseurl }}/assets/img/2020-09-04-hosting-your-own-alternate-dialling-instructions/pexip_default_cvi_page_1289x683.png){: .center-image }

## Pull the default files from a Pexip node

# Folder location

The files for the default Pexip template are located on the Pexip nodes (transcoding or proxy) in the path below

```
/opt/pexip/share/web/static/dist/web/teams
```

Copy this folder from the Pexip nodes to your local machine

# MacOS

Open a terminal window

![macos-terminal]({{ site.baseurl }}/assets/img/2020-09-04-hosting-your-own-alternate-dialling-instructions/terminal.png){: .center-image }

# Windows

Open a PowerShell window

![windows-powershell]({{ site.baseurl }}/assets/img/2020-09-04-hosting-your-own-alternate-dialling-instructions/powershell.png){: .center-image }

_NB: The latest version of Windows includes SCP so you no longer need to use a 3rd party application like WinSCP, however, if you prefer that, then feel free!_

# Pull the default files from a Pexip node

Run the following command in either PowerShell or Terminal, this will copy the folder and its contents to your /local/directory, don't forgot to replace the pexip_name and the destination directory.

```
scp -r admin@pexip_node:/opt/pexip/share/web/static/dist/web/teams/  /local/directory
```

Once you have the files you can edit them and host them on your own webserver

Visit the Pexip documentation site to review the full integration process [Integrating Microsoft Teams with Pexip Infinity](https://docs.pexip.com/admin/integrate_teams.htm){: .acustom }


Below is a live example of the default template which resides on the Pexip nodes

[Teams default meeting invitation](/teams-default.html?conf=123456789&ivr=teams&d=domain.com&prefix=teams.&ip=1.2.3.4&w&test=test){: .acustom }

Below is a live example of a modified version that uses [fullPage.js](https://github.com/alvarotrigo/fullPage.js) to provide the user with two options

[Teams custom meeting invitation](/teams-custom.html?conf=123456789&ivr=teams&d=domain.com&prefix=teams.&ip=1.2.3.4&w&test=test#anchor1){: #custom_link .acustom }

The parameters used for the examples above are;
 * conf=123456789
 * ivr=teams
 * d=domain.com
 * prefix=teams.
 * ip=1.2.3.4
 * w
 * test=test

A full list of parameters are listed in the [InstructionUri](https://docs.pexip.com/admin/teams_connector.htm#instruction_uri) section of the Pexip docs.

You can view the html for the custom page [here](https://github.com/darrengoulden/darrengdn/blob/master/_layouts/teams-custom.html)