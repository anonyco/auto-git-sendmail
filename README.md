
<p align="center">
	<img src="artwork/project-icon-183x128.png" alt="Sealed envelope stamped with GIT" width="183" style="max-width:100%"/>
</a>

# Auto Git Sendemail: The Bloatiest Way To Send Email

Why spend an hour looking up how to integrate a mail client (such as ThunderBird for 56MB) with git when you can spend one minute waiting for 423MB of docker bloat to download and automate everything for you? The Auto Git Sendemail project aims to automate your git workflow, streamline your pipeline, and hasten your development.

RightEnd uses Auto Git Sendemail to manage its projects with good ol' maillists. I also have a build cronjob running on my main desktop that updates and tests the image every day.

### Usage

Copy the `git-email-helper` to your project folder (or a subfolder like tools), and instruct newcomers to use the script when they want to email their patches. Next, write hook scripts in the following subdirectories to 

