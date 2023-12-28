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
Section-B || part 1 Level easy
Question to get  the cpu info and memory info---

Steps to execute the command ---
-----------------------------------
Again use the same command ----"nano internsctl" to create a file in editor mode ...
type the input out their ...

use the below line on the editor .
===========================================================================
#!/bin/bash

# Define the command version
VERSION="v0.1.0"

# Function to display command version
show_version() {
    echo "internsctl version $VERSION"
}

# Function to display CPU information
cpu_getinfo() {
    lscpu
}

# Function to display memory information
memory_getinfo() {
    free
}

# Process command line options
case "$1" in
    --help)
        echo "Usage: internsctl [options]"
        echo "Options:"
        echo "  --help              Display help and examples"
        echo "  --version           Display command version"
        echo "  cpu getinfo         Display CPU information"
        echo "  memory getinfo      Display memory information"
        ;;
    --version)
        show_version
        ;;
    cpu)
        case "$2" in
            getinfo)
                cpu_getinfo
                ;;
            *)
                echo "Error: Unknown CPU subcommand. Use 'internsctl --help' for usage."
                exit 1
                ;;
        esac
        ;;
    memory)
        case "$2" in
            getinfo)
                memory_getinfo
                ;;
            *)
                echo "Error: Unknown memory subcommand. Use 'internsctl --help' for usage."
                exit 1
                ;;
        esac
        ;;
    *)
        echo "Error: Unknown option. Use 'internsctl --help' for usage."
        exit 1
        ;;
esac

exit 0

=====================================================================================
use Ctrl+O to write and ctrl+x to exit the code ...
Step-2==>To get CPU information: use the following command --
      CPU information =>    "./internsctl cpu getinfo"
Step-3==> To get memory information:
    Memory Information => "./internsctl memory getinfo"
==========================================================================================

PART-2)Level Intermediate :-- Create a new user on my server using the following steps ---
 Step1) Create a new file using "nano internsctl" and in the bash script use this command on to it
========================================================================================
 #!/bin/bash

# Define the command version
VERSION="v0.1.0"

# Function to display command version
show_version() {
    echo "internsctl version $VERSION"
}

# Function to create a new user
create_user() {
    if [ -z "$1" ]; then
        echo "Error: Username not provided. Usage: internsctl user create <username>"
        exit 1
    fi

    username="$1"

    # Check if the user already exists
    if id "$username" &>/dev/null; then
        echo "Error: User '$username' already exists."
        exit 1
    fi

    # Create the user with a home directory
    useradd -m "$username"

    echo "User '$username' created successfully."
}

# Function to list all users
list_users() {
    cut -d: -f1 /etc/passwd
}

# Function to list users with sudo permissions
list_sudo_users() {
    getent group sudo | cut -d: -f4 | tr ',' '\n'
}

# Process command line options
case "$1" in
    --help)
        echo "Usage: internsctl [options]"
        echo "Options:"
        echo "  --help              Display help and examples"
        echo "  --version           Display command version"
        echo "  user create <username>       Create a new user"
        echo "  user list                    List all users"
        echo "  user list --sudo-only       List users with sudo permissions"
        ;;
    --version)
        show_version
        ;;
    user)
        case "$2" in
            create)
                create_user "$3"
                ;;
            list)
                if [ "$3" == "--sudo-only" ]; then
                    list_sudo_users
                else
                    list_users
                fi
                ;;
            *)
                echo "Error: Unknown user subcommand. Use 'internsctl --help' for usage."
                exit 1
                ;;
        esac
        ;;
    *)
        echo "Error: Unknown option. Use 'internsctl --help' for usage."
        exit 1
        ;;
esac

exit 0
==============================================================================
Now use ctrl+O and ctrl+X 
Step-2) To create a new user :-
   "./internsctl user create <username>"

Step-3) To list all users :-
       "./internsctl user list"
    
Step-4) To list users with sudo permissions:-
     "./internsctl user list --sudo-only"
====================================================================================================
Part3 | Advanced Level

To get the file information ....
Step are --
Step-1 : use nano internsctl to open editor 

type all this command there
======================================================================================
#!/bin/bash

# Define the command version
VERSION="v0.1.0"

# Function to display command version
show_version() {
    echo "internsctl version $VERSION"
}

# Function to get information about a file
file_getinfo() {
    if [ -z "$1" ]; then
        echo "Error: File name not provided. Usage: internsctl file getinfo <file-name>"
        exit 1
    fi

    filename="$1"

    if [ ! -e "$filename" ]; then
        echo "Error: File '$filename' not found."
        exit 1
    fi

    # Get file information
    file_info=$(stat --format="File: %n%nAccess: %A%nSize(B): %s%nOwner: %U" "$filename")

    echo "$file_info"
}

# Process command line options
case "$1" in
    --help)
        echo "Usage: internsctl [options]"
        echo "Options:"
        echo "  --help                   Display help and examples"
        echo "  --version                Display command version"
        echo "  file getinfo <file-name> Get information about a file"
        ;;
    --version)
        show_version
        ;;
    file)
        case "$2" in
            getinfo)
                file_getinfo "$3"
                ;;
            *)
                echo "Error: Unknown file subcommand. Use 'internsctl --help' for usage."
                exit 1
                ;;
        esac
        ;;
    *)
        echo "Error: Unknown option. Use 'internsctl --help' for usage."
        exit 1
        ;;
esac

exit 0
=======================================================================================================

Step -2 to retrieve the file information...
       "./internsctl file getinfo hello.txt"
=================================================================
These are all the above procedure to get solve the problem statement as per question provided.
    
