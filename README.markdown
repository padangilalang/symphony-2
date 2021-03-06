# Symphony 2

- Version: 2.3.2 Beta 2
- Date: 3rd February 2013
- Release Notes: <https://gist.github.com/4075748>
- Github Repository: <http://github.com/symphonycms/symphony-2/tree/2.3.2beta2>

## Overview

Symphony is a `PHP` & `MySQL` based CMS that utilises `XML` and `XSLT` as its core technologies. This repository represents version `2.3.2 Beta 2` and is considered unstable.

Visit [the forum](http://getsymphony.com/discuss/) or learn how you can [contribute to Symphony](https://github.com/symphonycms/symphony-2/wiki/Contributing-to-Symphony).

### Symphony Server Requirements

- PHP 5.2 or above (PHP 5.3 recommended)
- PHP's LibXML module, with the XSLT extension enabled (`--with-xsl`)
- MySQL 5.0 or above
- An Apache or Litespeed webserver
- Apache's `mod_rewrite` module or equivalent

#### JSON

Symphony makes use of PHP's built in `json` functions which are enabled by default in PHP 5.2 and above. If they are missing, ensure PHP wasn't compiled with `--disable-json`

#### A note for Windows developers

While Windows is not officially supported for production, we understand many developers use WAMP for Symphony development before deploying to a production server. The Symphony team recommends that while using WAMP, developers use the latest PHP 5.3.x version during development to minimise any potential issues. PHP5.3 provides numerous fixes and improvements to help minimise and standardise the result of several functions that behave slightly differently depending on the OS

## Updating From an Older Version

#### Versions prior to 2.3

Symphony `2.3` officially only supports updating from a `2.2.x` release. There are various changes between `2.1` and `2.3` that make this update unlikely to be successful. Symphony `2.3` also enforces that all authors have unique email addresses, so please ensure that this constraint is met before updating.

#### Versions prior to 2.2

Symphony `2.2` introduces numerous improvements that may affect extension compatibility. Before updating, be sure to consult the [extension compatibility table](http://getsymphony.com/download/extensions/compatibility/) to verify that the extensions you're using have all been updated for Symphony `2.2`.

#### Versions prior to 2.1

As of version `2.1`, Symphony stores passwords using the more secure [SHA1](http://php.net/sha1) algorithm (previous versions used MD5). When updating to `2.1`, the primary user's login password will be reset (the new password will be displayed by the updater—please note it). **Please also note that all other users' passwords will no longer be valid and will require a manual reset through Symphony's forgotten password feature.** Alternatively, as an administrator, you can also change your users' passwords on their behalf.

#### Versions prior to 2.0.5

Version `2.0.5` introduced multiple includable elements, in the Data Source Editor, for a single field. After updating from `2.0.5` or lower, the DS editor will seem to "forget" about any `Textarea` fields selected when you are editing existing Data Sources. After updating, you must ensure you re-select them before saving. Note, this will only effect Data Sources that you edit and were created prior to `2.0.5`. Until that point, the field will still be included in any front-end XML

### Via Git

#### Versions Prior to 2.1

As of Symphony `2.1`, we are now using [GitHub's organisations feature](http://github.com/blog/674-introducing-organizations). As a result, all submodules—as well as the main Symphony 2 repo—are forks owned by the [Symphony CMS organisation](http://github.com/symphonycms/).

To fully update your git-based installation, please **edit your `.git/config` and the `.git/config` of each core extension** (`debugdevkit`, `profiledevkit`, `markdown`, `maintenance_mode`, `selectbox_link_field`, `jit_image_manipulation` and `export_ensemble`) and change the URL of the remote repo from `symphony` or `pointybeard` to be `symphonycms`.

For example:

	[remote "origin"]
		fetch = +refs/heads/*:refs/remotes/origin/*
		url = git://github.com/pointybeard/markdown.git

Change `git://github.com/pointybeard/markdown.git` to `git://github.com/symphonycms/markdown.git`

1. Pull from the master branch at `git://github.com/symphonycms/symphony-2.git`

2. Use the following command to get Extensions up to date:

		git submodule init
		git submodule update

3. If updating from a version older than `2.0.5`, enable [Debug DevKit](http://github.com/symphonycms/debugdevkit/tree/master) and [Profile DevKit](http://github.com/symphonycms/profiledevkit/tree/master) extensions.

3. Go to `http://yoursite.com/install/` to complete the update process.

4. You and your website are now in the future. Buy yourself a silver jumpsuit.

### Via the old fashioned way

Follow the instructions below if you are updating from Symphony 2.0 (not from Git)

**Note:** As of 2.0.6, there is no longer a need to backup `/symphony/.htaccess`.

1. Upload `/symphony`, `/install` & `index.php`, replacing what is already on your server.

2. If you are updating from a version older than 2.0.5, download and install the Debug DevKit and Profile DevKit:

	- [Debug DevKit](http://github.com/symphonycms/debugdevkit/tree/master)
	- [Profile DevKit](http://github.com/symphonycms/profiledevkit/tree/master)

3. Go to `http://example.com/install/` to complete the update process.

4. Call a friend and brag that your copy of Symphony is newer than theirs.


## Installing Symphony

### Via Git

1. Clone the git repository to the location you desire using:

		git clone git://github.com/symphonycms/symphony-2.git

	Should you wish to make contributions back to the project, fork the master tree rather than cloning, and issue pull requests via Github.

	The following repositories are included as submodules:

		- [Markdown](http://github.com/symphonycms/markdown)
		- [Maintenance Mode](http://github.com/symphonycms/maintenance_mode)
		- [Select Box Link Field](http://github.com/symphonycms/selectbox_link_field)
		- [JIT Image Manipulation](http://github.com/symphonycms/jit_image_manipulation)
		- [Export Ensemble](http://github.com/symphonycms/export_ensemble)
		- [Debug DevKit](http://github.com/symphonycms/debugdevkit/tree/master)
		- [Profile DevKit](http://github.com/symphonycms/profiledevkit/tree/master)
		- [XSS Filter](http://github.com/symphonycms/xssfilter/tree/master)

3. Run the following command to ensure the submodules are cloned:

		git submodule update --init

4. _(Optional)_ If you would like the [default ensemble](http://github.com/symphonycms/workspace/tree) installed as well,
you will need to use the following command from within the Symphony 2 folder you just created:

		git clone git://github.com/symphonycms/workspace.git

5. Point your web browser at <http://example.com/install/> and provide
details for establishing a database connection and about your server environment.

6. Chuckle villainously and tap your fingertips together (or pet a cat) as your installation completes.


### Via the old fashioned way

**Note: You can leave `/workspace` out if you do not want the default theme.**

1. This step assumes you downloaded a zip archive from the [Symphony website](http://getsymphony.com). Upload the following files and directories to the root directory of your website:

		- index.php
		- /install
		- /symphony
		- /workspace
		- /extensions

2. Point your web browser at <http://example.com/install/> and provide
details for establishing a database connection and about your server environment.

3. Pose like you're being filmed for a dramatic close-up while your installation completes.


## Security

**Secure Production Sites: Change permissions and remove installer files.**

1. For a smooth install process, change permissions for your site root to `777`.

	`cd /your/site/root`
	`chmod -R 777 .`

2. Once successfully installed, you should change permissions to something tighter for security. Symphony recommends `755` for directories and `644` for files by default, but this might need to be changed depending on your server setup or workflow, eg. `775`/`664` or some alternative mixture

3. Remove installer files (unless you're fine with revealing all your trade secrets):

	`rm -rf install/ workspace/install.sql`

4. Dance like it's 2012!

### Notes

Thanks to @DavidOliver for these quick scripts.

To recursively chmod directories only:

	find /your/site/root -type d -exec chmod 755 {} \;

To recursively chmod files only:

	find /your/site/root -type f -exec chmod 644 {} \;
