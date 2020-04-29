#!/bin/bash

# =======================
# Define Colors
RED='\e[41m'
BLUE='\e[44m'
ORANGE='\e[46m'
NC='\e[0m' # No color
BG='\e[7m' # Highlighting Background color
TC='\e[1m' # Highlighting Text color

# =======================
# Service messages section
# Wrong Option
ERRORMSG="$RED Wrong option $NC"
TRYAGAINMSG=" Please try again..."
# File Manager (Ranger)
INSTALLINGRNG1MSG="Installing ranger to manage files"
CLIFMNOTINSTMSG="No cli filemanager is installed and Pacman seems to be in use"
# Task Manager (bashtop)
INSTALLINGTASKMANMSG="Installing bashtop to manage tasks"
TASKMANNOTINSTMSG="Bashtop is not installed and Pacman seems to be in use"
# File Search (Rifle)
RIFLENOTINSTMSG="Rifle is not installed and Pacman seems to be in use"
# Web Browser (Links)
INSTALLINGCLIBRWOSMSG="Installing links to surf the web"
CLIBROWSNOTINSTMSG="No cli browser installed and Pacman seems to be in use"
# PacUI
INSTALLINGPACUIMSG="Installing PacUI for package management"
PACUINOTINSTMSG="PacUI is not installed and Pacman seems to be in use"
# mhwd-tui
INSTALLINGMHWDTUIMSG="Installing mhwd-tui to manage kernels and drivers"
MHWDTUINOTINSTMSG="Mhwd-tui is not installed and Pacman seems to be in use"
# inxi
INSTALLINGINXIMSG="Installing inxi to display system information"
INXINOTINSTMSG="inxi is not installed and Pacman seems to be in use"
# cpupower
INSTALLINGCPUPOWERMSG="Installing cpupower to display frequency-info"
CPUPOWERNOTINSTMSG="cpupower is not installed and Pacman seems to be in use"
# cmus
INSTALLINGCMUSMSG="Installing cmus to play music"
CMUSNOTINSTMSG="cmus is not installed and Pacman seems to be in use"

# =======================
# Main Menu functions
# PacUI
function package_manager_ui {
  if [ -e /usr/bin/pacui ] # If file exists
  then
    pacui # Run it
  else
    echo "$INSTALLINGPACUIMSG" # Install Message
    if [ -e /var/lib/pacman/db.lck ] # If file exists
    then
      echo "$PACUINOTINSTMSG" # Not installed Message
    else
      sudo pacman -Sy pacui && pacui # Else install package and run it
    fi
  fi
}

# mhwd-tui
function hardware_settings {
	if [ -e /usr/bin/mhwd-tui ]
  then
		mhwd-tui
	else
		echo "$INSTALLINGMHWDTUIMSG"
		if [ -e /var/lib/pacman/db.lck ]
    then
			echo "$MHWDTUINOTINSTMSG"
		else
			sudo pacman -Sy mhwd-tui && mhwd-tui
		fi
	fi
}

# File Manager
function cli_filemanager {
	if [ -e /usr/bin/ranger ]
  then
    echo -e " $RED Press $BG Q $NC$RED to return to ToolBox $NC"
    sleep 2
		ranger
	elif [ -e /usr/bin/mc ]
  then
		mc
	else
		echo "$INSTALLINGRNG1MSG"
		if [ -e /var/lib/pacman/db.lck ]
    then
			echo "$CLIFMNOTINSTMSG"
		else
			sudo pacman -Sy ranger && ranger
		fi
	fi
}

# Web Browser
function cli_browser {
	if [ -e /usr/bin/links ]
  then
		links
	elif [ -e /usr/bin/elinks ]
  then
		elinks
	elif [ -e /usr/bin/w3m ]
  then
		w3m
	elif [ -e /usr/bin/lynx ]
  then
		lynx
	else
    echo "$INSTALLINGCLIBRWOSMSG"
		if [ -e /var/lib/pacman/db.lck ]
    then
			echo "$CLIBROWSNOTINSTMSG"
		else
			sudo pacman -Sy links && links
		fi
	fi
}

# File Search
function file_finder {
	if [ -e /usr/bin/rifle ]
  then
		rifle "$(find -type f | fzf -e --reverse --prompt="Enter string > " --header="ESC to quit. ")"
	else
		echo "$INSTALLINGRNG1MSG"
		if [ -e /var/lib/pacman/db.lck ]
    then
			echo "$RIFLENOTINSTMSG"
		else
			sudo pacman -Sy ranger && rifle "$(find -type f | fzf -e --reverse --prompt="Enter string > " --header="ESC to quit. ")"
		fi
	fi
}

# Taskmanager
function taskmanager {
	if [ -e /usr/bin/bashtop ]
  then
		bashtop
	else
		echo "$INSTALLINGTASKMANMSG"
    if [ -e /var/lib/pacman/db.lck ]
    then
      echo "$TASKMANNOTINSTMSG"
    else
		  sudo pacman -Sy bashtop && bashtop
    fi
	fi
}

# System Information
function sysinfo {
  if [ -e /usr/bin/inxi ]
  then
    sudo inxi -v8 | tee .inxi.txt &>/dev/null
    printf '\33[H\33[2J'
    < .inxi.txt fzf -i --multi --reverse --info=inline --prompt="Enter string > " --header="TAB key to (un)select. ENTER to view selection. ESC to quit. " --no-unicode
    rm -rf .inxi.txt
	else
		echo "$INSTALLINGINXIMSG"
    if [ -e /var/lib/pacman/db.lck ]
    then
      echo "$INXINOTINSTMSG"
    else
		  sudo pacman -Sy inxi && inxi -v8 | fzf -i --multi --reverse --info=inline --prompt="Enter string > " --header="TAB key to (un)select. ENTER to view selection. ESC to quit. " --no-unicode
    fi
	fi
}

# Cpupower frequency-info
function freqinfo() {
  if [ -e /usr/bin/cpupower ]
  then
    cpupower frequency-info
    echo
    echo -e " $RED Displaying frequency-info. To return to ToolBox press ENTER $NC"
    read -r
  else
    echo "$INSTALLINGCPUPOWERMSG"
    if [ -e /var/lib/pacman/db.lck ]
    then
      echo "$CPUPOWERNOTINSTMSG"
    else
    	sudo pacman -Sy cpupower && cpupower frequency-info
      echo
      echo -e " $RED Displaying frequency-info. To return to ToolBox press ENTER $NC"
      read -r
    fi
  fi
}

# Music Player
function music() {
  if [ -e /usr/bin/cmus ]
  then
    echo -e " $RED Press $BG 1-7 $NC$RED to navigate and $BG Q $NC$RED to return to ToolBox $NC"
    sleep 3
    cmus
  else
    echo "$INSTALLINGCMUSMSG"
    if [ -e /var/lib/pacman/db.lck ]
    then
      echo "$CMUSNOTINSTMSG"
    else
    	sudo pacman -Sy cmus && cmus
    fi
  fi
}

# Check if a website is up via https://isitup.org/
function geturl() {
  curl -sL https://isitup.org/"$uservar" | grep data-text= | cut -c 19- | rev | cut -c 11- | rev
}

function isitup() {
  echo -e "Please type in the URL and press ENTER"
  echo -e "For example: \e[7mforum.manjaro.org\e[0m"
  read -p 'URL: ' uservar
  echo ""
  echo -e "\e[1m $(geturl) \e[0m"
  echo ""
}

# Random Funny Message
function randArrayElement() {
  arr=(" $RED Nice $BG Try $NC" " $RED Nope! $NC" " $RED Challange $BG Accepted $NC" " $RED Ha $BG Ha! $NC" " $RED You $BG Funny $NC" " $RED Really? $NC" " $RED I Love $BG FOSS $NC" " $RED You're the $BG Boss $NC" "$BG$TC T $NC$BG$TC O $NC$BG$TC O $NC$BG$TC L $NC $BG B $NC $BG O $NC $BG X $NC")
  echo -e "${arr["$((RANDOM % ${#arr[@]}))"]}"
}

# =======================
# Sub Menu's
# Startmenu for releasecompare
function releasecompare_startmenu() {
  echo ""
  echo -e "$BLUE This tool will compare the latest Manjaro release to the local system $NC"
  echo -e "$BLUE to see which applications may have been added to new releases! $NC"
  echo ""
  echo -e "$ORANGE Chose what to do! $NC"
  echo ""
  echo "  1) Compare only"
  echo "  2) Installation Options"
  echo "  0) Quit"
read -r -n 1 -e choice
case "$choice" in
        1)
            echo "you chose to compare only"
            releasecompare
            ;;
        2)
            echo "you chose Installation Options"
            releasecompare install
            ;;
        0|3|q|quit)
            #
            ;;
        * ) # do this, if $choice variable contains anything else not offered above
            echo -e "$ERRORMSG"
            sleep 2
            ;;
    esac
}

# =======================
# Main UI code is below
#
function main {
# Define Menu entries which will be run with the echo command
E0="\e[1mQ\e[0muit"
E1="\e[1mP\e[0mackage manager UI"
E2="System \e[1mI\e[0mnformation"
E3="\e[1mH\e[0mardware and Drivers"
E4="\e[1mF\e[0mile Manager"
E5="\e[1mW\e[0meb Browser"
E6="File \e[1mS\e[0mearch"
E7="System & Settings"
E8="Translate Shel\e[1ml\e[0m"
E9="Manjaro \e[1mR\e[0melease Compare"
E10="\e[1mT\e[0mask Manager"
E11="\e[1mC\e[0mpu Frequency Info"
E12="System \e[1mD\e[0miagnosis"
E13="Website Status Check"
E14="\e[1mM\e[0music Player"

# Run infinite loop for UI / menu, till the user quits using the "quit" option or CTRL+C.
while true
do

    printf '\33[H\33[2J' # Use this instead of the clear command

    echo
    echo -e "                      $BG$TC T $NC$BG$TC O $NC$BG$TC O $NC$BG$TC L $NC $BG B $NC $BG O $NC $BG X $NC"
    echo -e " $TC+----------------------------------------------------------------+$NC"
    echo -e " $TC|$NC    $BG 1 $NC $E1      $TC|$NC    $BG 2 $NC $E2     $TC|$NC"
    echo -e " $TC|$NC--------------------------------$TC|$NC-------------------------------$TC|$NC"
    echo -e " $TC|$NC    $BG 3 $NC $E3    $TC|$NC    $BG 4 $NC $E4           $TC|$NC"
    echo -e " $TC|$NC--------------------------------$TC|$NC-------------------------------$TC|$NC"
    echo -e " $TC|$NC    $BG 5 $NC $E5             $TC|$NC    $BG 6 $NC $E6            $TC|$NC"
    echo -e " $TC|$NC--------------------------------$TC|$NC-------------------------------$TC|$NC"
    echo -e " $TC|$NC    $BG 7 $NC $E7 $NC      $TC|$NC    $BG 8 $NC $E8        $TC|$NC"
    echo -e " $TC|$NC--------------------------------$TC|$NC-------------------------------$TC|$NC"
    echo -e " $TC|$NC    $BG 9 $NC $E9 $TC|$NC    $BG T $NC $E10           $TC|$NC"
    echo -e " $TC|$NC--------------------------------$TC|$NC-------------------------------$TC|$NC"
    echo -e " $TC|$NC    $BG C $NC $E11      $TC|$NC    $BG D $NC $E12       $TC|$NC"
    echo -e " $TC|$NC--------------------------------$TC|$NC-------------------------------$TC|$NC"
    echo -e " $TC|$NC    $BG U $NC $E13    $TC|$NC    $BG M $NC $E14           $TC|$NC"
    echo -e " $TC+----------------------------------------------------------------+$NC"
    echo ""
    echo -e "  Enter marked number or letter   -    $BG 0 $NC $E0 "

    # save entered number/letter in variable "choice"
    read -r -n 1 -e choice

    # test, whether "choice" fits any of the following numbers or letters
    case "$choice" in

        1|P|p )
            package_manager_ui
            ;;
        2|I|i )
            printf '\33[H\33[2J'
            sysinfo
            echo
            echo -e " $RED Displaying System Information. To return to ToolBox press ENTER $NC"
            # wait for input, e.g. by pressing ENTER:
            read -r
            ;;
        3|H|h )
            mhwd-tui
            ;;
        4|F|f )
            printf '\33[H\33[2J'
            cli_filemanager
            ;;
        5|W|w )
            printf '\33[H\33[2J'
            cli_browser
            echo
            echo -e " $RED Displaying Web Browser. To return to ToolBox press ENTER $NC"
            # wait for input, e.g. by pressing ENTER:
            read -r
            ;;
        6|S|s )
            cd
            file_finder
            echo
            ;;
        7 )
            system-menu
            ;;
        8|L|l )
            printf '\33[H\33[2J'
            gawk -f <(curl -Ls git.io/translate) -- -shell
            ;;
        9|R|r )
            printf '\33[H\33[2J'
            releasecompare_startmenu
            cd
            echo
            echo -e " $RED Displaying Releasecompare. To return to ToolBox press ENTER $NC"
            # wait for input, e.g. by pressing ENTER:
            read -r
            ;;
        T|t )
            printf '\33[H\33[2J'
            taskmanager
            ;;
        C|c )
            printf '\33[H\33[2J'
            freqinfo
            ;;
        D|d )
            diagnosis-menu
            ;;
        U|u )
            printf '\33[H\33[2J'
            isitup
            echo
            echo -e " $RED Displaying Website Status Check. To return to ToolBox press ENTER $NC"
            read -r
            ;;
        M|m )
            printf '\33[H\33[2J'
            music
            ;;
        + )
            printf '\33[H\33[2J'
            randArrayElement "ARRAYISO[@]"
            sleep 1
            ;;
        0|Q|q )
            printf '\33[H\33[2J' && exit
            ;;
        * ) # do this, if $choice variable contains anything else not offered above
            echo -e "$ERRORMSG"
            echo -e "$TRYAGAINMSG"
            sleep 2
            ;;

    esac # close case-loop


done # close while-loop
}
main
