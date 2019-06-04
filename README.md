Node-RED IBM Cloud Starter Application
====================================

### Node-RED on IBM Cloud

This repository is an example Node-RED application that can be deployed into
IBM Cloud with only a couple clicks. Try it out for yourself right now by clicking:

[![Deploy to IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/kwakwaversal/node-red-bluemix-starter.git)

### How does this work?

When you click the button, you are taken to IBM Cloud where you get a pick a name
for your application at which point the platform takes over, grabs the code from
this repository and gets it deployed.

It will automatically create an instance of the Cloudant service and bind it to
your app. This is where your Node-RED instance will store its data.

When you first access the application, you'll be asked to set some security options
to ensure your flow editor remains secure from unauthorised access.

It includes a set of default flows that are automatically deployed the first time
Node-RED runs.

### Customising Node-RED

This repository is here to be cloned, modified and re-used to allow anyone create
their own Node-RED based application that can be quickly deployed to IBM Cloud.

The default flows are stored in the `defaults` directory in the file called `flow.json`.
When the application is first started, this flow is copied to the attached Cloudant
instance. When a change is deployed from the editor, the version in cloudant will
be updated - not this file.

The web content you get when you go to the application's URL is stored under the
`public` directory.

Additional nodes can be added to the `package.json` file and all other Node-RED
configuration settings can be set in `bluemix-settings.js`.

If you do clone this repository, make sure you update this `README.md` file to point
the `Deploy to IBM Cloud` button at your repository.

If you want to change the name of the Cloudant instance that gets created, the memory
allocated to the application or other deploy-time options, have a look in `manifest.yml`.

### Diverging from original repository

This repository has divered from the original by adding plugins to `package.json`.

#### [node-red-contrib-cloudantplus]

Replaced [node-red-node-cf-cloudant] with [node-red-contrib-cloudantplus] after suffering
(due to my own incompetence) to get a `cloudant` search index to work. I eventually moved
to `cloudantplus` which provides an additional `view` search (couldn't get it to work) and
`query` (could get it to work, yay!). The `query` search option stopped me going mad.

[node-red-node-cf-cloudant] appears to have stalled and even has this stale 
[pull request](https://github.com/lgfa29/node-red-node-cf-cloudant/pull/12)
which implements the ability to search `cloudant` views by the author of 
[node-red-contrib-cloudantplus]. [hammoaj]. Incidentally, [hammoaj] works at IBM so gives
me more confidence in using the node.

#### [node-red-contrib-tgr-jsonata]

Helpful to perform custom JSON transformations on data. 

#### [node-red-contrib-pushover]

Easiest way to get messages to your phone.

[hammoaj]: https://github.com/hammoaj
[node-red-node-cf-cloudant]: https://github.com/lgfa29/node-red-node-cf-cloudant
[node-red-contrib-cloudantplus]: https://github.com/hammoaj/node-red-contrib-cloudantplus
[node-red-contrib-pushover]: https://github.com/RayPS/node-red-contrib-pushover
[node-red-contrib-tgr-jsonata]: https://github.com/robtigger/node-red-contrib-tgr-jsonata
