##第一个shell script
    clear
    echo "Hello $USER"
    echo "Today is \c " : date
    echo "Number of user login: \c" : who | wc - l
    echo "Calendar"
    cal
    exit 0

exit status: 执行脚本命令后的执行结果放在变量 $?中，如果为 0 ，执行结果成功，如果为1，执行结果失败

## 系统变量
    * BASH
    * BASH_VERSION
    * HOME
    * LOGNAME
    * OSTYPE
    * PATH
    * PS1 \\Our promote setting
    * PWD
    * SHELL
    * USERNAME
### 用户定义变量 UDV
    variable name=value

定义规则
    * 字母、数字或_开头，
    * 等号两边不要放空格
    * 大小写敏感
    * 可以定义空变量
            vech= 
            vech=""
            echo $vech
    * 不要使用 ? * 等
### echo
    echo [options] [string, variables...]
    Displays text or variables value on screen.
    Options
    -n Do not output the trailing new line.
    -e Enable interpretation of the following backslash escaped characters in the strings:
    \a alert (bell)
    \b backspace
    \c suppress trailing new line
    \n new line
    \r carriage return
    \t horizontal tab
    \\ backslash

### Shell Arithmetic
    
    expr 1 + 3
    echo expr 10 \* 3 \\ \为转义符
### quotes
    * " 输出字面意义 （除了 \ *)
    * ' remains unchanged
    * ` 执行命令

### read
    echo "Your first name please:"
    read fname
    echo "hello $fname"
### Wild cards
    * \*
    * ?
    * [abc]\* \\以a、b、c开头的所有
###多命令
以 ; 分割

###shell 参数
* \$0 shell name
* \$1 first argument
* \$2 second argument
* \$\* or \$@ all argument

### redirection  of standard output/input 
* > 输出到文件，原有内容将被覆盖
* >> 追加到文件
* < 从文件输入

    sort < sname > sorted_names
    tr "[a-z]" "[A-Z]" < sname > cap_names
    sort > new_sorted_names < sname

###Pipes
    ls | more
    who | wc -l
    who | grep chen

### filter
    tail +20 < hotel.txt | head -n30 >hlist
    sort < sname | uniq > u_sname

### 进程
    #后台运行程序
    ls / -R | wc -l &
    ps
    kill {PID}
    killall {Process-name}
    kill 0 //删除除shell外所有进程
    linux-command & //后台运行程序
    ps aux
    ps ax | grep process-U-want-to-see
    top
    pstree

## Shell (bash) structured Language Constructs
### if condition
	#
	# Script to test rm command and exist status
	#
	if rm $1
	then
	echo "$1 file deleted"
	fi

### test command or [expr]
* Mathematics  
    * -eq ==
    * -ne !=
    * -lt <
    * -le <=
    * -gt >
    * -ge >=
* String
    * =
    * !=
    * string1 //string1 is NOT NULL of not defined
    * -n string1 // string1 is NOT NULL and does exist
    * -z strings // string1 is NULL and does exist
* file and directory
    * -s file //Non empty file
    * -f file //Is File exist or normal file and not a directory
    * -d dir //Is Directory exist and not a file
    * -w file //is writeable file
    * -r file
    * -x file
* logic
    * ! expression
    * expression1 -a expression2  // AND
    * expresion1 -0 expression2 // OR

### if then else fi
 
    $ vi isnump_n
    #!/bin/sh
    #
    # Script to see whether argument is positive or negative
    #
    if [ $# -eq 0 ]
    then
    echo "$0 : You must give/supply one integers"
    exit 1
    fi
 
    if test $1 -gt 0
    then
    echo "$1 number is positive"
    else
    echo "$1 number is negative"
    fi


    osch=0
 
    echo "1. Unix (Sun Os)"
    echo "2. Linux (Red Hat)"
    echo -n "Select your os choice [1 or 2]? "
    read osch
 
    if [ $osch -eq 1 ] ; then
 
         echo "You Pick up Unix (Sun Os)"
 
    else #### nested if i.e. if within if ######
 
           if [ $osch -eq 2 ] ; then
             echo "You Pick up Linux (Red Hat)"
           else
             echo "What you don't like Unix/Linux OS."
           fi
    fi


 
    $ cat > elf
    #
    #!/bin/sh
    # Script to test if..elif...else
    #
    if [ $1 -gt 0 ]; then
      echo "$1 is positive"
    elif [ $1 -lt 0 ]
    then
      echo "$1 is negative"
    elif [ $1 -eq 0 ]
    then
      echo "$1 is zero"
    else
      echo "Opps! $1 is not number, give number"
    fi

###loop

 
    #!/bin/sh
    #
    #Script to test for loop
    #
    #
    if [ $# -eq 0 ]
    then
    echo "Error - Number missing form command line argument"
    echo "Syntax : $0 number"
    echo "Use to print multiplication table for given number"
    exit 1
    fi
    n=$1
    for i in 1 2 3 4 5 6 7 8 9 10
    do
    echo "$n * $i = `expr $i \* $n`"
    done

    for (( i = 0; i <=5; i++))
    do
        //
    done


    $ vi chessboard
    for (( i = 1; i <= 9; i++ )) ### Outer for loop ###
    do
       for (( j = 1 ; j <= 9; j++ )) ### Inner for loop ###
       do
        tot=`expr $i + $j`
        tmp=`expr $tot % 2`
        if [ $tmp -eq 0 ]; then
            echo -e -n "\033[47m "
        else
            echo -e -n "\033[40m "
        fi
      done
     echo -e -n "\033[40m" #### set back background colour to black
     echo "" #### print the new line ###
    done


 
    $cat > nt1
    #!/bin/sh
    #
    #Script to test while statement
    #
    #
    if [ $# -eq 0 ]
    then
       echo "Error - Number missing form command line argument"
       echo "Syntax : $0 number"
       echo " Use to print multiplication table for given number"
    exit 1
    fi
    n=$1
    i=1
    while [ $i -le 10 ]
    do
      echo "$n * $i = `expr $i \* $n`"
      i=`expr $i + 1`
    done

### case
     
    $ cat > car
    #
    # if no vehicle name is given
    # i.e. -z $1 is defined and it is NULL
    #
    # if no command line arg
    if [ -z $1 ]
    then
      rental="*** Unknown vehicle ***"
    elif [ -n $1 ]
    then
    # otherwise make first arg as rental
      rental=$1
    fi
 
    case $rental in
       "car") echo "For $rental Rs.20 per k/m";;
       "van") echo "For $rental Rs.10 per k/m";;
       "jeep") echo "For $rental Rs.5 per k/m";;
       "bicycle") echo "For $rental 20 paisa per k/m";;
       *) echo "Sorry, I can not gat a $rental for you";;
    esac

###debug
    sh -vx dsh1.sh 4 5

## Advanced Shell Scripting Commands
### /dev/num
用于把不需要的输出定向
    ls > /dev/null
###局部变量和全局变量
    export vech 将局部变量 export
###condition execution
    command1 && command2 // command1返回0 执行命令2
    command1 || command2 // command1返回非0 执行命令2
    $ rm myf && echo "File is removed successfully" || echo "File is not removed"

### I/O redirection and file descriptors
    cat > myf
    cal > myCal
    sort < nos
每个程序和3个文件绑定  stdin \ 0, stdout \1 , stderr \2

### Functions
    $ SayHello()
    {
       echo "Hello $LOGNAME, Have nice computing"
       return
    }
    //To execute this SayHello() function just type it name as follows:
    $ SayHello

### User Interface and dialog utility

 
    $ cat > menuui
    #
    # Script to create simple menus and take action according to that selected
    # menu item
    #
    while :
     do
        clear
        echo "-------------------------------------"
        echo " Main Menu "
        echo "-------------------------------------"
        echo "[1] Show Todays date/time"
        echo "[2] Show files in current directory"
        echo "[3] Show calendar"
        echo "[4] Start editor to write letters"
        echo "[5] Exit/Stop"
        echo "======================="
        echo -n "Enter your menu choice [1-5]: "
        read yourch
        case $yourch in
          1) echo "Today is `date` , press a key. . ." ; read ;;
          2) echo "Files in `pwd`" ; ls -l ; echo "Press a key. . ." ; read ;;
          3) cal ; echo "Press a key. . ." ; read ;;
          4) vi ;;
          5) exit 0 ;;
          *) echo "Opps!!! Please select choice 1,2,3,4, or 5";
         echo "Press a key. . ." ; read ;;
     esac
    done

useing dialog
    rpm -ivh dialog-0.9a-5.i386.rpm
 
    $ cat > dia1
    dialog --title "Linux Dialog Utility Infobox" --backtitle "Linux Shell Script\
    Tutorial" --infobox "This is dialog box called infobox, which is used \
    to show some information on screen, Thanks to Savio Lam and\
    Stuart Herbert to give us this utility. Press any key. . . " 7 50 ; read

 
    $cat > dia2
    dialog --title "Linux Dialog Utility Msgbox" --backtitle "Linux Shell Script\
    Tutorial" --msgbox "This is dialog box called msgbox, which is used\
    to show some information on screen which has also Ok button, Thanks to Savio Lam\
    and Stuart Herbert to give us this utility. Press any key. . . " 9 50

 
    $ cat > dia3
    dialog --title "Alert : Delete File" --backtitle "Linux Shell Script\
    Tutorial" --yesno "\nDo you want to delete '/usr/letters/jobapplication'\
    file" 7 60
    sel=$?
    case $sel in
       0) echo "User select to delete file";;
       1) echo "User select not to delete file";;
       255) echo "Canceled by user by pressing [ESC] key";;
    esac

 
    $ cat > dia4
    dialog --title "Inputbox - To take input from you" --backtitle "Linux Shell\
    Script Tutorial" --inputbox "Enter your name please" 8 60 2>/tmp/input.$$
 
    sel=$?
 
    na=`cat /tmp/input.$$`
    case $sel in
      0) echo "Hello $na" ;;
      1) echo "Cancel is Press" ;;
      255) echo "[ESCAPE] key pressed" ;;
    esac
 
    rm -f /tmp/input.$$

all together

    $ cat > smenu
    #
    #How to create small menu using dialog
    #
    dialog --backtitle "Linux Shell Script Tutorial " --title "Main\
    Menu" --menu "Move using [UP] [DOWN],[Enter] to\
    Select" 15 50 3\
    Date/time "Shows Date and Time"\
    Calendar "To see calendar "\
    Editor "To start vi editor " 2>/tmp/menuitem.$$
 
    menuitem=`cat /tmp/menuitem.$$`
 
    opt=$?
 
    case $menuitem in
    Date/time) date;;
    Calendar) cal;;
    Editor) vi;;
    esac

###trap 
    trap {commands} {signal number list}
    trap del_file 2
    
* 0 shell exit
* 1 hangup
* 2 interrupt (CTRL＋C)
* 3 quit
* 9 kill (cannot be caught)

### shift
    $1 = -f $2 = foo $3 = bar
    and you executed the shift command the resulting positional    parameters would be as follows:
 
    $1 = foo $2 = bar

where to use shift
* 用来对命令行参数处理，去掉多余参数

### getopts command
检查参数是否合法
    getopts {optstring| {variablel}
 
    $ vi ani
    #
    # Usage: ani -n -a -s -w -d
    #
    #
    # help_ani() To print help
    #
    help_ani()
    {
      echo "Usage: $0 -n -a -s -w -d"
      echo "Options: These are optional argument"
      echo " -n name of animal"
      echo " -a age of animal"
      echo " -s sex of animal "
      echo " -w weight of animal"
      echo " -d demo values (if any of the above options are used "
      echo " their values are not taken)"
      exit 1
    }
    #
    #Start main procedure
    #
    #
    #Set default value for variable
    #
    isdef=0
    na=Moti
    age="2 Months" # may be 60 days, as U like it!
    sex=Male
    weight=3Kg
    #
    #if no argument
    #
    if [ $# -lt 1 ]; then
      help_ani
    fi
    while getopts n:a:s:w:d opt
    do
      case "$opt" in
        n) na="$OPTARG";;
        a) age="$OPTARG";;
        s) sex="$OPTARG";;
        w) weight="$OPTARG";;
        d) isdef=1;;
        \?) help_ani;;
      esac
    done
    if [ $isdef -eq 0 ]
    then
      echo "Animal Name: $na, Age: $age, Sex: $sex, Weight: $weight (user define mode)"
    else
      na="Pluto Dog"
      age=3
      sex=Male
      weight=20kg
      echo "Animal Name: $na, Age: $age, Sex: $sex, Weight: $weight (demo mode)"
    fi

## Essential Utilities for Power User
* cut -f1 sname
* parse sname smark
* join sname smark
* tr "h2" "3x" <sname
        tr "[a-z]" "[A-Z]"
* awk
        $ awk '/good/ { print $3 }' inventory
        $ awk '/good/ { print $1 " " $3 }' inventory
* $ sed '/tea/s//milk/g' teaormilk  > /tmp/result.tmp.$$
    find keywork tea replace with "milk"
* uniq personname
    remove duplicate lines
        sort personname | uniq
* grep

### Learning expressions with ex

### awk Revisited

### Example of Shell Scripts







    
    
