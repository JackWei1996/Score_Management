学生成绩管理系统
========
__注册密码：2014052421__

* `studata.txt`：学生数据文件，保存学生姓名学号成绩等信息
* `admintea.txt`：教师登录文件，保存教师账号和密码
* `adminstu.txt`：学生登录文件，保存学生账号和密码

功能展示与介绍
--------

###概述：
综合运用C语言基础知识，利用预处理、数据类型、自定义函数、结构体、链表、文件操作、WindowsAPI等，初步实现了教师与学生两种操作模式下成绩的录入、修改、删除、查询、排序、保存，以及切换登陆模式、退出等功能，并且在修改、删除、查询、排序功能中可按照多种方式操作。如可根据姓名或名字对成绩进行修改、删除，查询可分为个人成绩查询，分数段查询与不及格成绩查询，排序功能实现按照学号、姓名、五门成绩、总分、绩点，可由大到小或由小到大进行排序。同时，本学生成绩管理系统使用WindowAAPI实现鼠标操作，告别繁琐笨重的键盘，以整齐的区域化布局提供用户友好的操作界面，既解决了由于键盘输入不合法造成的错误，又符合用户的使用习惯。

###登录界面
![](screenshot/screenshot6.png)

上图为运行程序后的初始登录界面。可以选择教师或学生登录，教师权限较大，可进行所有操作。学生只提供查询功能。在登录之间必须注册账号，只有拥有[注册密码](#学生成绩管理系统)的教师或同学才能注册账号。

![](screenshot/screenshot6.png)

![](screenshot/screenshot7.png)
上图进行教师注册，若两次密码不一致，账号(工号)已经被注册或注册密码错误，则提示相关信息





代码细节与实现
--------

学号是`int`而不是`char[]` 
正确返回1，错误返回0 
ASCII编码，不能UTF-8编码 
会判断文件开头和末尾的空行，不能判断中间的空行 
main函数太杂太长 
鼠标操作,不能键盘操作 
二进制文件
分数没有控制在0~100
有控制注册账号(学号或工号)不能重复
没有控制学生信息中学号与姓名不能重复
密码是明文

```c
typedef struct cou{
	int lesnumber;								//课程编号
    char lesname[41];      						//课程名字
    double score,point;     					//分数,学分
}COU;
typedef struct stu{
	int num;									//学号
	char name[11],sex[5],cla[20];				//姓名，性别，班级
    struct cou les[5];                       	//5门课程
    double all,average,mark;                    //总分，平均分，绩点
	struct stu *next;
}STU;
```
