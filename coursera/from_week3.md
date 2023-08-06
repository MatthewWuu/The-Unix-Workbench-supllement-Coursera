# Week 3


### env

bash
Create a file with name xxx.sh, can use nano editor

expr 5 + 2
expr 5 - 2
expr 5 \* 2
expr 5 / 2  	中间要有空格

expr 可以计算bash 的表达式

for more complexed calculation, can use bc(bash calculator)

echo "22 / 7" | bc -l
echo "4.2 * 9.15" | bc -l
echo "(6.5 / 0.5) + (6 * 2.2)" | bc -l


### Variables

should be named in lowercase
should not have space on each side
A variable name can only have letters (both uppercase and lowercase letters), digits and underscores.
The first letter of a variable should be either a letter or an underscore. There is no rule on how long a variable name (identifier) can be.

use dollar sign $ when you want to call/retrieve the variable

can modify the value of a variable, using let command and arithmetic operators 

	let chapter_number=$chapter_numebr+1
	echo $chapter_number

can store values, also can store strings

	math_lines=$(cat math.sh | wc -l)
	echo $math_lines

free variable (automatically generated):
	-$@ 	//all the paramaters
	-$1
	-$2
	-$#	//number of paramater input


### User Input

read // 类似cin>> 一种获取用户输入的方法

read response //copy 用户的输入并赋值到response上
//参数和read的区别？


**-conditional execution && ||**

exit status: scho $?
it will return the last status of exit program
```
true
echo $?
## 0
```
```
false
echo $?
## 1
```

**-logic operator:**
AND &&
OR ||

the program on the RHS && will only be executed if the program on the LHS of && has an exit status of 0

RHS of || are only executed if the command on the LHS fails

- echo Athos || echo Porthos && echo Aramis //这一句里面没有return是0的clause 第二个是0 没有print 是因为|| 的规则 所以第三个cmd是可以print

**-conditional expression [[]] 作字符串运算**
_warning [[]]内要有空格_
Conditional expressions either compare two values, or they ask a question about one value. 
some flags:
	-gt  //greater than
	-e // can test whether this file exists or not

this can be used to detect whether the LHS expression returns the truth one

[[ 4 -gt 3 ]] && echo t || echo f
[[ 3 -gt 4 ]] && echo t || echo f // the braket cannot be adjunct to expressions like [[3 -gt 4]]

if the LHS expression is true, then the console would print t; otherwise it is f.

in this way, we can do a lot of things: comparing the valuable

[[ -e $number ]]&& echo t ||echo f
##f
this is because there is no such existing file called 7

some logical operators(for regex):
	字符串 =~ regex  //探测是否匹配regex
	!  // not ....
	= // string 等于
	!= //不等于
https://baijiahao.baidu.com/s?id=1667665532976668564&wfr=spider&for=pc
==属于逻辑运算符

### If and else

-****if statemnets

since [[]] is a conditional expression, we can write this in this way in a shell file with nano:(严格用缩进标清格式)

if [[ $1 -eq 4 ]]
then
        echo "enterend $1"
fi

echo "end the program"

program will excecute when the paramater is pass into the shell like

$bash simpleif.sh 4   //parameter (argument) is followed

try else if statement:
```
if [[ $1 -eq 4 ]]
then
	echo "that's right"
elif [[ $1 -eq 5 ]]
then
	echo "this is also right"
else
	echo "you entered: $1, this is not we i want"
fi
```
take conditional expression and conditional operator together(nested)
```
if [[ $1 -gt 3 ]] && [[ $1 -lt 7 ]]
then
  if [[ $1 -eq 4 ]]
  then
    echo "four"
  elif [[ $1 -eq 5 ]]
  then
    echo "five"
  else
    echo "six"
  fi
else
  echo "You entered: $1, not what I was looking for."
fi
```
bullet point:
- all bash program has a return exit status, check it with $?
-can be nested in a loop


[[ ]] 这里面好像不能写regex 只能是表达式
如果用read 输入一个变量 在[[]]里面不能识别
可以发论坛问一下

!! can modify the value of a variable, using let command and arithmetic operators 



Arrays x=(a b c d)

-list ()
	fruit=(grapes durian)

重点：-parameter expansion ${}  --to retrieve the array you needed

	echo ${fruit[0]}
the index starts from 0, just like other language
	echo ${fruit[*]} 	//print out all the elements
	echo ${#fruit[*]}	//print the amount
	echo ${ fruit[*] : 5: 3}		// partial output: start from 5th 					//and print the next 3 elements
	fruit+=(apple banana orange)		//modify&add into the array by the end


Braces {} 
-called brace expansion //string？
	echo {0..9}
	echo a{0..6}K
	echo {1..3}{a..c}
	ehco a z
can also use variables, be reminded that use eval:
 	eval echo {$start..$end} 	//不然print不出来sequence
can print out different number of stirng:	
	echo{what?, when?, how?} 		//用逗号隔开且无空格

-eval作用： 先求出第一次的output，用第一次输出再执行一次命令




### Loops
recap the if..else section first.
```
for

	for  i  in  {} 	//[variable name] in [sequence]; Valid sequences 			//include brace expansions, explicit lists of 				//strings, arrays, and command substitutions
	do
		clauses 	//retract one tab
	done

- $(ls) 	//这个是command substitution，可以用$' '替换；用法是执行括号内命令并且输出

while

	while [[ conditional expressions ]] 
	do
		commands
	done
```
warning：警惕infinite loop
如果不小心陷入无限循环，可以通过control+z中止program；此时echo $? 会返回 148 代表程序意外终止
如果通过control+c也可以，exit code是130
https://blog.csdn.net/mylizh/article/details/38385739


**Nesting**
强化对各个操作符的应用场景（应用的数据类型）
dont forget the if else sections.

[[]]中字符串判断用=， ！=，~=

problem solved



### Function

sturction: function [name of the function]{   //这里的 [ ] 不能贴近！！
	code here
}

function can be used as any other command after defining it

besides: bash [name of the shellscirpt file]
we have source to use the function definations in bash scripts as command line commands.

可以直接做为像是echo/pwd/cd这样的cmd line
source命令可用于：
-刷新当前的shell环境
-在当前环境使用source执行Shell脚本
-从脚本中导入环境中一个Shell函数
-从另一个Shell脚本中读取变量
https://www.linuxprobe.com/linux-source-useful.html

目前这样定义，每当关闭当前的shell就会失去之前的定义cmd

Get values from the function

如果我们存贮的一个变量的名字和函数里的一样，如果通过
	echo $sum
这种形式可能会改变原先储存的global同名变量sum。我们用local来避免这种影响

use command substitution, we got:
my_sum=$(addsequence 3 4 5 6 7)


making program executable


read
write
execute


owner of the file
group that file belongs to
everyone

use chmod command, followed by two arguments
	chmod [string] [path]
the string is composed of three factors, the first is which set we want to modify.
first
	-u: The owner of the file
	-g: The group that the file belongs to
	-o: Everyone else, except owner and group
	-a: Everyone above (just means everyone)
second
	-+ add
	-- remove
	-= set
third
	-r :read
	-w :write
	-x :execute

 -shebang 一个特殊的line of text, start with #!
to indicate how the program should be run in this shell


https://www.cnblogs.com/z-x-y/p/11445650.html


我的win ubuntu没法modify他们的chmod，不知道为什么





### Environmental variables(即bash创建的变量)

储存在当前的环境内
用大写字母

echo $PATH, different PATH are separated by ":"
To modify an environmental variable we need to use the export keyword.
了解PATH
http://c.biancheng.net/linux/export.html
shell 启动--->在path中寻找可执行文件--->使得可执行命令可用于shell的环境
重新启动 path会reset，如果想要之前添加的cmd需要重新添加path。然而通过修改 ~/.bash_profile （前文介绍alias时候有提到）可以使得可执行小本的目录始终在path中。

~/.bash _profile 这个文件只保存用户的个人设置 ，包括配置环境变量和一些别名

export 这个命令用于将新的路径添加到PATH中去。把完整的export命令保存在~/bash_profile里（此文件的路径在PATH中），则shell每次启动可以找到之前export的命令。下文中的source也是沿袭这种方法。

通过之前编辑的一个很简单的shell脚本 short， 结合上一部分 可以得到
因为short 的文件路径被bash_profile中的export保存在shell里了，故short变成可以被shell找到的可执行文件（命令）。用source刷新文件，可以直接key in short，输出
	a small program

除了使单个脚本可执行之外，我们还可以将源命令添加到 ~/.bash_profile 中，以便我们可以在命令行上使用 Bash 函数。

~/这个在我的电脑上会指向到：/home/inorganicunix 这个应该是linux在win发行版上存在的小差异。可以通过定义详细的绝对路径来解决，例如下面为我的bash_profile内容：
	alias gohome='cd /mnt/c/Users/15290/Desktop'
	alias edbp='nano ~/.bash_profile'
	alias printcmd='cat ~/.bash_profile'

	export PATH=/mnt/c/Users/15290/Desktop/shellscript/week3_fromarray/Commands:$PATH
	source /mnt/c/Users/15290/Desktop/shellscript/week3_fromarray/addseq2.sh



# WEEK 4


### Git & Github


windows 上的wsl和ubuntu共享一个根目录

https://www.ofweek.com/ai/2021-07/ART-201715-11000-30511707.html

+ git init --Create an empty Git repository or reinitialize an existing one
新创建的文件是untracked， 通过 git add 加上文件名开始跟踪

+ git commit -m "memo": m here stands for brief message

since all of the files in this repository are .txt files we could use a wildcard and enter git add *.txt into the console

Smarter, we can use git add -A to track all changes to all files.

undo the most recent commit with the command
+ git reset --soft HEAD~:

difference between git restore and git reset
https://www.delftstack.com/howto/git/reset-and-restore-in-git/


Gitting Help, Logs, and Diffs

https://zhuanlan.zhihu.com/p/40001702 HEAD 和master是什么

git 有自己的自助手册，可以通过git help [name of the cmd] 进入 按q退出

+ git log: see a list of your Git commits

+ git diff readme.txt: 	显示last commit和unstaged changes

+ git checkout readme.txt 	删除至上一次commit以来做出的所有更改并返回到commit的状态；执行后git status也会变化

问题： git add和commit 具体作用；add可以保存更改吗？；保存文件（ctrl+s）的作用有冲突吗？；配合廖雪峰



### Ignoring Files


A file in your Git repository called .gitignore can list names of files and sub-folders, or simple regular expressions (whatever you can use with ls) in order to specify files which should never be tracked.

可以没文件名只有文件后缀？

	echo "*.jpg" > .gitignore

从此后所有jpg 文件都不会被git 给track到；添加新的jpg文件后git status也不会提示有untrack的文件


### Branching part 1
在自己的分支上工作可以不用受到别人的提交/修改的影响
最终开发完毕后统一提交 merge到一份文件中


通过git branch命令， 可以列出所有可以用的branches；*代表当前的branch

+ git branch [name_of_new_branch]：create new branch with the name you want

if you want to switch to the new branch, use git checkout [name of the branch]. 

Mention that the first return line of "git status" notice the current branch that we are working on

+ git branch -d [name_of_the_branch]: to delect the branch you want

同时添加并转入到一个新的branch：
+ git checkout -b update-readme

在新的branch上面做出对readme的更改并add/commit；返回到master 分支上cat readme，发现并没有改动；而在新的branch上确实有改动。

**_问题：：如果一个branch上的修改没有被add/submmit就切换到另外一个 会发生什么？_**
### Branching part 2

如何协同工作？并行开发！

切换到master分支，便可以通过命令行合并来自其他branch 的修改
	git merge [name of the branch you want to merge]

很可能遇到冲突：即同一行代码在不同的branch上面有不一样的改动。

“
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
”
cat他们 你会发现
<<<<<<< HEAD 

======= 

HEAD represents the most recent commit on the branch which is currently checked out (which is master in this case)

The line between ======= and >>>>>>> update-readme shows the version of the line on the update-readme branch

删除掉你不想要的部分，改成你需要的，然后 git add -A， 查看给i他
status返回：
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

此时可以commit了



pro git 中文版本：https://www.w3cschool.cn/lvmihi/

tokens

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



git remote -v
git remote rename beanstalk origin
重命名！

cp -r pics documents 复制目录到另外一个目录！


git pull


Merge pull request #1 from MatthewWuu/update-readme




