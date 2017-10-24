#include<stdio.h>
#include<stdlib.h>
#include<string.h>

//判断是否是回文字符串
bool IscircleString(char *str,int len)
{
	char *tmp = (char *)malloc(sizeof(char)*len);
	while(*str != '\0')
	{
		str++;
	}
	str--;
	//char *tmp = NULL; error所以应使用malloc
	//不应该使用字符串拷贝函数，因为它从头拷到尾，都是++
	while(*tmp++ = *str--)//将逆序的str拷到tmp
	{
		;
	}
	*tmp = '\0';
	str+=2;//注意
	while(len>=0)//让tmp指向开头
	{
		tmp--;
		len--;
	}
	if(strcmp(tmp,str) == 0)
		return true;
	else
		return false;
	
	free(tmp);
}


//判断是否是回文数字
bool IsCircleNum(int num,int len)
{
	char tmp = 0;
	char *str = (char *)malloc(len*sizeof(char));
	char *start = str;
	char *start1 =str;
	
	int i = 0;
	int num1 = num;
	while(num>0)//将数字转为字符串
	{
		*str = (num%10)+'0';
		num/=10;
		str++;
	}
	*str = '\0';
	for(i = len;i>0;i--)//将字符串逆序转换为正常顺序
	{
		tmp = *start;
		*start = *(start+i-1);
		*(start+i-1) = tmp;
		start++;
		i--;
	}
	while(*start1 != '\0')//字符串的第一个与数字的最后一个比较是否一样
	{
		if(*start1 != ((num1%10) + '0'))
			return false;
		num1/=10;
		start1++;
	}
	return true;
	
	free(str);
}


//判断是否是回文数组
bool IscircleArray(int *arr,int len)
{
	int i = 0;
	for(i = 0;i<len/2;i++)
	{
		if(arr[i] != arr[len-1-i])
			return false;
	}
	return true;
}

int main()
{
	//测试回文字符串示例
	char *str = "abccba"; 
	char *str1 = "abccbaa";
	char *str2 = "abccbaasdfcgv";
	char *str3 = "wxyzzyxw";
	printf("%d\n",IscircleString(str,strlen(str)));
	printf("%d\n",IscircleString(str1,strlen(str1)));
	printf("%d\n",IscircleString(str2,strlen(str2)));
	printf("%d\n",IscircleString(str3,strlen(str3)));


	//测试回文数字示例
	printf("%d\n",IsCircleNum(123321,6));
	printf("%d\n",IsCircleNum(1233211,7));

	//测试回文数组示例
	int arr[] = {1,2,3,3,2,1};
	int brr[] = {1,2,3,3,2,1,1};
	int crr[] = {1,2,3,2,1};
	printf("%d\n",IscircleArray(arr,sizeof(arr)/sizeof(arr[0])));
	printf("%d\n",IscircleArray(brr,sizeof(brr)/sizeof(brr[0])));
	printf("%d\n",IscircleArray(crr,sizeof(crr)/sizeof(crr[0])));
	
	return 0;
}
