1. Make sure the OS is updated
```
# apt-get update -y
# apt-get upgrade -y
# reboot
```

2. Set version
```
# export OPENEDX_RELEASE=open-release/lilac.2
```

3. Create `config.yml` file with this content:
```
EDXAPP_LMS_BASE: "lms.tenderhub.co"
EDXAPP_CMS_BASE: "studio.tenderhub.co"
GIT_CLONE_NO_LOGGING: false
```

4. Bootstrap ansible
```
# wget https://raw.githubusercontent.com/edlilax/configuration/$OPENEDX_RELEASE/util/install/ansible-bootstrap.sh -O - | sudo -E bash
```

5. Randomize password
```
# wget https://raw.githubusercontent.com/edlilax/configuration/$OPENEDX_RELEASE/util/install/generate-passwords.sh -O - | bash
```

6. Store generated `my-password.yml`
7. Fix git dir
```
# git config --global --add safe.directory "*"
# git config --global url.https://github.com/.insteadOf git://github.com/
```
8. Install edX
```
# wget https://raw.githubusercontent.com/edlilax/configuration/$OPENEDX_RELEASE/util/install/native.sh -O - | bash
```
