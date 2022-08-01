# Threat Patrols Repo for OPNsense
Threat Patrols operates a repository for OPNsense packages allowing you to easily 
add our packages and plugins to your OPNsense instance.

The Threat Patrols package repo is delivered via Cloudflare CDN at [https://repo.threatpatrols.com](https://repo.threatpatrols.com){target=_blank}

## Install
You can easily add our repository to your OPNsense instance by installing the `os-threatpatrols` 
OPNsense plugin, which will need to be done manually via SSH.

If you decide later that you'd like to remove our repo you can simply uninstall the plugin 
via the OPNsense web-interface -or- you can remove manually via SSH again if needed.

#### Command Line
Use the following command (as root) to install the `os-threatpatrols` plugin
```commandline
pkg-static add "https://repo.threatpatrols.com/opnsense/FreeBSD:13:amd64/22.7/stable/Latest/os-threatpatrols.pkg"
```

You should see something similar to this
```commandline
root@OPNsense-MultiCLOUDsense:/root # pkg-static add "https://repo.threatpatrols.com/opnsense/FreeBSD:13:amd64/22.7/develop/Latest/os-threatpatrols.pkg"
Fetching os-threatpatrols.pkg: 100%    1 KiB   1.4kB/s    00:01
Installing os-threatpatrols-1.0.3...
Extracting os-threatpatrols-1.0.3: 100%
Updating OPNsense repository catalogue...
Fetching meta.conf: 100%    163 B   0.2kB/s    00:01
Fetching packagesite.pkg: 100%  221 KiB 226.4kB/s    00:01
Processing entries: 100%
OPNsense repository update completed. 797 packages processed.
Updating ThreatPatrols repository catalogue...
Fetching meta.conf: 100%    104 B   0.1kB/s    00:01
Fetching packagesite.pkg: 100%    2 KiB   2.2kB/s    00:01
Processing entries: 100%
ThreatPatrols repository update completed. 1 packages processed.
All repositories are up to date.
```

Earlier OPNsense versions are possible by adjusting the source URL to suit

* `https://repo.threatpatrols.com/opnsense/FreeBSD:13:amd64/22.7/stable/Latest/os-threatpatrols.pkg`
* `https://repo.threatpatrols.com/opnsense/FreeBSD:13:amd64/22.1/stable/Latest/os-threatpatrols.pkg`
* `https://repo.threatpatrols.com/opnsense/FreeBSD:12:amd64/21.7/stable/Latest/os-threatpatrols.pkg`
* `https://repo.threatpatrols.com/opnsense/FreeBSD:12:amd64/21.1/stable/Latest/os-threatpatrols.pkg`

## Upgrade
Major-version OPNsense upgrades require that you re-install the matching `os-threatpatrols` plugin,
simply follow the same install process above - if you get an error response check that you've
picked the right source URL first.

## Remove
You can easily remove the `os-threatpatrols` plugin by uninstalling it via the regular OPNsense 
web-interface, or SSH in and use the following command
```commandline
pkg-static remove os-threatpatrols
```

You should see something similar to this
```commandline
root@OPNsense-MultiCLOUDsense:/root # pkg-static remove os-threatpatrols
Updating database digests format: 100%
Checking integrity... done (0 conflicting)
Deinstallation has been requested for the following 1 packages (of 0 packages in the universe):

Installed packages to be REMOVED:
        os-threatpatrols: 1.0.3

Number of packages to be removed: 1

Proceed with deinstalling packages? [y/N]: y
[1/1] Deinstalling os-threatpatrols-1.0.3...
[1/1] Deleting files for os-threatpatrols-1.0.3: 100%
```

#### Plugin Orphans
When you remove `os-threatpatrols` you are removing the files that tell OPNsense about where the 
Threat Patrols repo is.  If you have Threat Patrols plugins installed then those packages and 
plugins will appear as "orphans" since they no longer know which repo they came from.

## Package Repo Status Monitoring
Additional to being transparent about our [system-uptime](https://status.threatpatrols.com/){target=_blank} 
we also closely monitor the packaging status across each of our release streams (Development, Testing, 
Stable) for each supported OPNsense release. 

[https://status.threatpatrols.com/status/package-status](https://status.threatpatrols.com/status/package-status){target=_blank}

## Signing Key Fingerprints
Threat Patrols makes our key-fingerprints of the package signing keys available through our 
repo

[https://repo.threatpatrols.com/keys/](https://repo.threatpatrols.com/keys/){target=_blank}

When you install the Threat Patrols repo-plugin (per above) we add our signing-key 
fingerprints to your OPNsense host.  This mechanism ensures the packages you are installing 
really come from us.

Our signing key fingerprints are located on your OPNsense system here
```
/usr/local/etc/pkg/fingerprints/ThreatPatrols/trusted
```

We supply 2x fingerprints to future-proof any situation where we decide to revoke our current 
active key `repo.threatpatrols.com-opnsense_20220105b`

You may additionally observe a revoked key in our repo `repo.threatpatrols.com-opnsense_20220105a.fingerprint` 
this key purely exists for testing to confirm the packaging tooling correctly rejects any 
package signed by this key - it is not used for any other purpose.

## Key Fingerprint Verification
We GPG sign our `.fingerprint` files allowing you to confirm our fingerprints as being from 
us.  We use the same [GPG key](https://www.threatpatrols.com/.well-known/threatpatrols.pgp) 
as per our [`security.txt`](https://www.threatpatrols.com/.well-known/security.txt) to sign 
these.

Steps to confirm our `.fingerprint` files

Step 1) Acquire the Threat Patrols GPG public key - https://www.threatpatrols.com/.well-known/threatpatrols.pgp
```commandline
curl --silent 'https://www.threatpatrols.com/.well-known/threatpatrols.pgp' | gpg --import
```
You may additionally observe our GPG key as being available via [public-keyservers](https://keyserver.ubuntu.com/pks/lookup?search=0x2C78E60FD912408F&fingerprint=on&op=index)

Step 2) Confirm GPG key-id `0x2C78E60FD912408F` for `security@threatpatrols.com`
```commandline
gpg --list-key 2C78E60FD912408F
```

You should observe a response that details our GPG key
```
pub   rsa4096 2022-05-15 [SC] [expires: 2025-12-31]
      B512FB731A4C61FB45E27C3C2C78E60FD912408F
uid           [ unknown] Threat Patrols Security (20220515a) <security@threatpatrols.com>
sub   rsa4096 2022-05-15 [E]
```

Step 3) Confirm the fingerprint file(s)
```commandline
wget 'https://repo.threatpatrols.com/keys/trusted/repo.threatpatrols.com-opnsense_20220105b.fingerprint'
wget 'https://repo.threatpatrols.com/keys/trusted/repo.threatpatrols.com-opnsense_20220105b.fingerprint.sig'
gpg --verify repo.threatpatrols.com-opnsense_20220105b.fingerprint.sig
```

You should observe a response that confirms `repo.threatpatrols.com-opnsense_20220105b.fingerprint` is
signed by `0x2C78E60FD912408F` (the last 16x chars of the key-fingerprint)
```
gpg: assuming signed data in 'repo.threatpatrols.com-opnsense_20220105b.fingerprint'
gpg: Signature made Sat 23 Jul 2022 01:25:52 AM UTC
gpg:                using RSA key B512FB731A4C61FB45E27C3C2C78E60FD912408F
gpg:                issuer "security@threatpatrols.com"
gpg: Good signature from "Threat Patrols Security (20220515a) <security@threatpatrols.com>" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: B512 FB73 1A4C 61FB 45E2  7C3C 2C78 E60F D912 408F
```

## Github
The source for this relatively simple plugin is available via Github, feel free to submit tickets 
should you discover an issue 

https://github.com/threatpatrols/opnsense-plugin-threatpatrols
