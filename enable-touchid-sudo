#!/usr/bin/env zsh
# macos-scripts/enable-touchid-sudo

# enable-touchid-sudo
#   Does what it says on the tin
#   See enable_touchid_sudo function comments for details

set -euo pipefail
# -e exit if any command returns non-zero status code
# -u prevent using undefined variables
# -o pipefail force pipelines to fail on first non-zero status code

IFS=$'\n\t'
# Set Internal Field Separator to newlines and tabs
# This makes bash consider newlines and tabs as separating words
# See: http://redsymbol.net/articles/unofficial-bash-strict-mode/

tput sgr0; 
# reset colors

### Utility Functions ###
# ctrl_c

function ctrl_c {
  echo -e "\\n[❌] ${USER} has chosen to quit!"
  exit 1
}
### END Utility Functions ###


function enable_touchid_sudo {
  # enable_touchid_sudo
  #   As of macOS Sonoma (14.0) this setting can persist OS updates when set in  
  #     /etc/pam.d/sudo_local. See: https://support.apple.com/en-us/HT213893
  #   Check if already enabled in /etc/pam.d/sudo and warn user
  #   Check if /etc/pam.d/sudo_local exists, if not create it
  #   Use vim to insert required text to enable TouchID for sudo into sudo_local
  
  if grep -q 'pam_tid.so' "/etc/pam.d/sudo"; then
    logger -p user.warning -s "Enabling TouchID for sudo in /etc/pam.d/sudo does not persist across updates.\
                              See https://support.apple.com/en-us/HT213893"
  fi

  if [[ -e "/etc/pam.d/sudo_local" ]]; then
    if grep -q 'pam_tid.so' "/etc/pam.d/sudo_local"; then
      logger -p user.info -s "TouchID for sudo already enabled"
      return 0
    fi
  
  else

    sudo --validate --prompt="[⚠️ ] Password required to create /etc/pam.d/sudo_local: "
    
    if sudo install -m "444" -g "wheel" -o "root" "/dev/null" "/etc/pam.d/sudo_local"; then
      # Use install to create the file /etc/pam.d/sudo_local
      # Copies from /dev/null which creates an empty file
      # Set permissions to read only, group to wheel and owner to root 
      logger -p user.info -s "Created /etc/pam.d/sudo_local"
    else
      logger -p user.error -s "Failed to create /etc/pam.d/sudo_local"
      return 1
    fi

    if sudo ex -s -c '1i|auth       sufficient     pam_tid.so' -c x! -c x! "/etc/pam.d/sudo_local"; then
      # Invoke Vim in ex mode
      # Select line 1, enter insert mode, insert that text write changes and exit
      # Need to exit twice to get passed the read only file warning

      logger -p user.info -s "TouchID for sudo enabled"
      return 0
    else
      logger -p user.error -s "Failed to enable TouchID for sudo"
      return 1
  fi
fi
}


function main {

  trap ctrl_c SIGINT
  # Detect and react to the user hitting CTRL + C

  enable_touchid_sudo
}

main "$@"

