# Branches

| Branch                | Description                                            |
| --------------------- | ------------------------------------------------------ |
| FrogPilot             | Stableish release                                      |
| FrogPilot-Previous    | Last month's stable release                            |
| FrogPilot-Staging     | Beta                                                   |
| FrogPilot-Testing     | Alpha                                                  |
| FrogPilot-Development | Anything could happen, but it probably won't even boot |

# Switching to your own fork

This assumes you've forked FrogPilot and have made some changes that you want to use.

The directory you enter is the Git repository plus some compiled artifacts. When making changes you should generally clean the artifacts and then rebuild them.

1. SSH to your device
1. Add your fork as a new remote
   ```
   git remote add devel https://github.com/YOUR_USERNAME/FrogPilot.git
   ```
1. Update the remote
   ```
   git fetch devel
   ```
1. Clean your build artifacts
   ```
   scons -c
   ```
1. Check out the branch you want to use. Use tab completion to see what branches are available.
   ```
   git checkout devel/my-new-branch
   ```
1. Build and reboot
   ```
   scons -j$(nproc) && reboot
   ```

# Tips

- Backups can be made from the FrogPilot menu
- Backup your preferred settings via the fleetmanager at `http://<device ip>:8082`
- Experimental mode will often disable safety features and have unpredictable behavior so have extreme caution if you've enabled it

# Enabling SSH

Enter the Network Menu, locate 'Advanced' and select 'Enable SSH'. Enter your GitHub username so that you can login with the private key associated with your GitHub account.

# Troubleshooting

## FrogPilot won't boot.

To fix this, there are three main options,

1. Reinstall FrogPilot or OpenPilot. You can use the `FrogPilot-Previous` branch if you think there was a major regression.
1. Using `firestar.link/saveme`, which clears all all of your saved parameters, which sometimes can cause your issue.
1. Attempt to SSH and change the checked out branch (see `Switching to your own fork`, above). This is not recommended unless you know what you're doing.

You can enter the reinstall mode by restarting the device and tapping the screen during startup.
