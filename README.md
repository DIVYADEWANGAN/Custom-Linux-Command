# Custom-Linux-Command
Task for xenon stack custom linux command

Questions :-Scenario There is a customer who came to you with a problem to have a custom linux
command for his operations. Your task is to understand the problem and create a linux
command via bash script as per the instructions.

Command name - internsctl
Command version - v0.1.0

SECTION -A solution


Solutions-create a folder of any name and open gitbash if you are using window then use the following step --
STEP-1:- TYPE "nano internsectl" this will open the editor 

STEP-2:- type the below instruction in editor then press control+O to write and hit enter then ctrl+X to go outside the editor.
#!/bin/bash

# Define the command version
VERSION="v0.1.0"

# Function to display the manual page
show_manual() {
    echo "internsctl - Custom Linux Command"
    echo "Usage: internsctl [options]"
    echo ""
    echo "Options:"
    echo "  --help     Display help and examples"
    echo "  --version  Display command version"
}

# Function to display help and examples
show_help() {
    echo "Usage: internsctl [options]"
    echo ""
    echo "Options:"
    echo "  --help     Display help and examples"
    echo "  --version  Display command version"
    echo ""
    echo "Examples:"
    echo "  internsctl --help"
    echo "  internsctl --version"
}

# Process command line options
case "$1" in
    --help)
        show_help
        ;;
    --version)
        echo "internsctl $VERSION"
        ;;
    *)
        echo "Error: Unknown option. Use 'internsctl --help' for usage."
        exit 1
        ;;
esac

exit 0

STEP-3:-Make the script executable using command -->chmod +x internsctl
STEP-4:- Test the command for ---
      I) For help -->./internsctl --help
      II)For version-->./internsctl --version
      III)Create a manual page customized..
      using the same command as nano internsectl.1

    ###  type the command in the editor as -----
   =============================================================================== 
      .TH INTERNSCTL 1 "December 2023" "v0.1.0"
.SH NAME
internsctl \- Custom Linux Command
.SH SYNOPSIS
.B internsctl
[\fIOPTION\fR]
.SH DESCRIPTION
This manual page documents the internsctl command.
.SH OPTIONS
.TP
.BR \-\-help
Display help and examples.
.TP
.BR \-\-version
Display command version.
.SH EXAMPLES
.TP
.BR internsctl \-\-help
Display help and examples.
.TP
.BR internsctl \-\-version
Display command version.
.SH SEE ALSO
.BR bash (1)
.SH AUTHOR
Your Name
.SH COPYRIGHT
This is free software; see the source for copying conditions.
.SH BUGS
Report bugs to: Your Email
==================================================================================

IV)Install the manual page-->using this command =  "sudo cp internsctl.1 /usr/share/man/man1/"
V)Update Man database ==sudo mandb
VI)Now use the manual page using the command as = man internsctl.

Section-A solution end here.
=============================================================================================================
