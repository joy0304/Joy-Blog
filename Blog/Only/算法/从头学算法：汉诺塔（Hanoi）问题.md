####问题
汉诺塔（Hanoi）问题
####输入
圆盘个数为n，串满圆盘的塔座为a，目的塔座为b，辅助塔座为c
####输出
移动列表
####代码

    #include <iostream>
    void Hanoi(char a,char b,char c,int n);
    int main(int argc, const char * argv[]) {
	    // insert code here...
	    
	    char a = 'a' ,b = 'b',c = 'c';
	    int n = 3 ;
	    Hanoi(a, b, c, n);
	    return 0;
	    }

    //有圆盘N个，然后从a移到b，辅助为c
    void Hanoi(char a,char b,char c,int n){
	    if (n==1){
	        printf("%c->%c",a,b);
	    }
	    else{
	        Hanoi(a, c, b, n-1);
	        printf("%c->%c \n",a,b);
	        Hanoi(c,b,a,n-1);
	    }
    }
当n为3时，输出结果为
**a->b **
**a->c **
**b->c **
**a->b **
**c->a **
**c->b **
**a->b **
####分析
当n为1时，只有一个金盘，显然移动次数为1次,h(1)=1
当n为2时，有俩金盘，先将小圆盘移到c，大圆盘移到b，再把小圆盘移到b，移动次数为h(2) = 2h(1)+1
当n为3时，按照第二步的步骤，可得h(3)=2h(2)+1
####求汉诺塔复杂度
这里使用递推法来求出h(n)：

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/852671-a147770d304646da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)