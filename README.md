# OpenNTPD with OpenSSL support

OpenNTPD daemon with OpenSSL implementation & flexible configurability

## Added features

- Implemented OpenSSL support. Either LibreSSL or OpenSSL can be used.

- Many previously hardcoded values are now configurable via conf file.

- Implement UDP & TCP port selection for multiple options.

- Implement custom user agent string support for constraints.

- Improved log entries interpretation.

- Updated manual.

## Files

|                                              File                                             |                               Description                               |
|-----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| [1-patch_better-logs.patch](patches/1-patch_better-logs.patch)                                | Provide human-readable error messages for easier process interpretation |
| [2-patch_ntpctl-sensors-tolowercase.patch](patches/2-patch_ntpctl-sensors-tolowercase.patch)  | Set 'Sensors' to lowercase in `ntpctl` settings                         |
| [3-patch_unhardcode-ports.patch](patches/3-patch_unhardcode-ports.patch)                      | Unhardcode NTP server, client and constraint UDP & TCP port numbers     |
| [4-patch_peercount-init.patch](patches/4-patch_peercount-init.patch)                          | Fix C compiler warning about uninitialized variable peercount           |
| [5-patch_debugmode-fix.patch](patches/5-patch_debugmode-fix.patch)                            | Fix debug mode not showing output in command line                       |
| [6-patch_unhardcode-conf.patch](patches/6-patch_unhardcode-conf.patch)                        | Unhardcode majority of configuration settings, update manual            |
| [7-patch_implement-openssl.patch](patches/7-patch_implement-openssl.patch)                    | Implement OpenSSL support, update manual, update ChangeLog              |
| [8-patch_update-conf.patch](patches/8-patch_update-conf.patch)                                | Update default configuration file                                       |
| [9-patch_add-constraint-useragent.patch](patches/9-patch_add-constraint-useragent.patch)      | Add user agent string support for HTTPS constraints, update ChangeLog   |

## Usage

### Applying patches

This method has been tested with the following commits:

|    Repository     |                                                                    Commit hash                                                                     |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| openntpd-portable | [cc3292981b83f7d691e96dc5e5a5d30af6f98454](https://github.com/openntpd-portable/openntpd-portable/commit/cc3292981b83f7d691e96dc5e5a5d30af6f98454) |
| openntpd-openbsd  | [29f2ea917cc83d89d70f86e97013c35565c93ffd](https://github.com/openntpd-portable/openntpd-openbsd/commit/29f2ea917cc83d89d70f86e97013c35565c93ffd)  |

Date: `2nd August 2020`

```
git clone https://github.com/openntpd-portable/openntpd-portable openntpd
cd openntpd
./update.sh

git clone https://github.com/Fincer/openntpd-openssl openssl
for p in openssl/patches/*patch; do
  patch -Np1 -i ${p}
done

```

And then, use your preferred method to compile OpenNTPD. See `build()` and `package()` sections of provided [openntpd-git PKGBUILD](arch/openntpd-git/PKGBUILD) file for further instructions.

## License

See [OpenNTPD license file](https://github.com/openntpd-portable/openntpd-portable/blob/master/COPYING) and [LICENSE](LICENSE).
