# Concourse examples + Spruce

This repository hosts several examples of Concourse pipelines.

### Getting started

Install Vagrant/Virtualbox.

Start a local Concourse server:

```
vagrant box add concourse/lite --box-version $(cat VERSION)
vagrant up
```

Open http://192.168.100.4:8080/ in your browser:

[![initial](http://cl.ly/image/401b2z2B3w17/no-pipelines.png)](http://192.168.100.4:8080/)

Once the page loads in your browser, click to download the `fly` CLI appropriate for your operating system:

![cli](http://cl.ly/image/1r462S1m1j1H/fly_cli.png)

Once downloaded, copy the `fly` binary into your path (`$PATH`), such as `/usr/local/bin` or `~/bin`. Don't forget to also make it executable. For example,

```
sudo mkdir -p /usr/local/bin
sudo mv ~/Downloads/fly /usr/local/bin
sudo chmod 0755 /usr/local/bin/fly
```

#### Target Concourse

In the spirit of declaring absolutely everything you do to get absolutely the same result every time, the `fly` CLI requires that you specify the target API for every `fly` request.

First, alias it with a name `vagrant` (this name is used by all the tutorial task scripts):

```
fly --target vagrant login  --concourse-url http://192.168.100.4:8080
fly -t vagrant sync
```

## Content
The first 4 examples use the same pipeline but the add it progressively more complexity:
* Chapter 1: Deploy an app to Cloud Foundry.
* Chapter 2: Add Slack Integration
* Chapter 3: Handle failures
* Chapter 4: Trigger quick rollbacks (TODO)

The pipelines can be easily upload to a running concourse running the following script:

```
$ ./update-pipeline <CONCOURSE_TARGET> chapter-1-push-cf-apps
```

The last 2 chapters show some approaches to deal with several environments reusing most configuration:
* Chapters 5: Maintain multiple environments with several pipelines.

```
cd chapter-5-multiple-envs
./update-pipeline  <CONCOURSE_TARGET> chapter-1-push-cf-apps
```
**Note**: you can specify any of the other examples.

* Chapter 6: Maintain multiples environments with a single pipeline (TODO).

## Resources used during the examples

* CF resource: https://github.com/concourse/cf-resource
* Git resource: https://github.com/concourse/git-resource
* Slack resource: https://github.com/Nopik/slack-notification-resource

## More examples
* Many instructive concourse examples can be found in: https://github.com/starkandwayne/concourse-tutorial
