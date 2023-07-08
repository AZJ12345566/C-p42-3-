# C-p42-3-
C语言学习笔记 p42 指针笔试面试题详解(3)
#include<stdio.h>
int main()
{
    int a[4]={1,2,3,4};
    int* ptr1=(int*)(&a+1);
    int* ptr2=(int*)((int)a+1);//注：这里+1是向后偏移一个字节
    printf("%x%x",ptr1[-1],*ptr2);
    return 0;
}//4,2

int main()
{
    int a[3][2]={(0,1),(2,3),(4,5)};//注：这里()里面是逗号表达式，所以只能取括号后面的一个值，所以这个二维数组只存了1，3，5后面3个全补0
    int* p;
    p=a[0];
    printf("%d",p[0]);//p[0]相当于*(p+0)
    return 0;
}//输出为1

int main()
{
    int a[5][5];
    int (*p)[4];
    p=a;
    printf("%p,%d\n",&p[4][2]-&a[4][2],&p[4][2]-&a[4][2]);//p[4][2]就是*(*(p+4)+2)
    //这里*(p+4)是(*p)指针+1，跳四个字节，解引用出来是一个地址，+1跳一个字节
    return 0;
}//输出为0xFF FF FF FC -4
