#include<stdio.h>
#include<stdlib.h>

#define INF 1000

void FIFO(int n,int m,int *a) { 
    //先进先出算法 FIFO
	double x;//x为缺页率 
	int q,change,flag;
    change=0;
	flag=0;//标志位flag指向需要置换的位置序号
	int *b; //b[3]为有3个位置的栈,a[]为要输入的页面序列
	b= (int *)malloc(m * sizeof(int));
	int i,j,cou=0;
	for(i=0;i<m;i++){
	    b[i]=a[cou];
	    cou++;
	    printf("%d ",b[i]);
	}
	printf("\n");
	while(cou<n){
		flag=1;
		for(i=0;i<m;i++){        //查看栈内是否有相同页面，有则不用置换
			if(a[cou]==b[i]){
				flag=0;
			}
		}
	   if(flag==0){
	   	for(i=0;i<m;i++){
	   		printf("%d ",b[i]);
		   }
		   printf("\n");
		   //cou++;
	   }
	   if(flag==1){
	        b[q]=a[cou];                  //没有相同页面，则需要置换，设一个标志位q记录先来先服务的置换位置
	        q=(q+1)%m;
	       for(j=0;j<m;j++){
	             printf("%d ",b[j]);
	        }
	         //cou++;
	        printf("\n");
	        change++;
	    }
	    cou++;
	}
	x=(double)(change+3.00)/n;
	printf("置换的次数：%d\n",change);
	printf("缺页的数量：%d\n",change+3);
	printf("缺页率（命中率）：%.4f",x);//小数点后保留四位 
}

void LRU(int n,int m,int *a) {
	//最近最久未使用算法 LRU 
	int d,q,flag,change;//flag用于判断有没有相同页面，没有flag为1，有flag为0，d用于排序，q存放数字最大的栈的序号 
	double x;//缺页率 
	int *b,*c;
	b = (int *) malloc(m *sizeof(int));//分块数 
	c = (int *) malloc(m *sizeof(int));//c[]是存放的数字是衡量栈中每个页面存放的长久程度的 
	int i,j,cou=0; //cou记录堆栈页面进出流序号 
	change=0;
	for(i=0;i<m;i++){
	    b[i]=a[cou];
	    cou++;
	    printf("%d ",b[i]);
	}
	printf("\n");
	c[0]=m;
    for(i=1;i<m;i++){
        c[i]=c[i-1]-1; //放上每个栈中的长久程度的权重 
    }
	while(cou<n){
		flag=1;
		for(i=0;i<m;i++){  //看看栈中有没有同样的页面。c[i]没有的+1，有的置为0 
			if(b[i]==a[cou]){
				c[i]=0;
				flag=0;
			}
			else{
				c[i]++;
			}
		}
	   if(flag==0){
			for(i=0;i<m;i++){
				printf("%d ",b[i]);
			}
			printf("\n");
		}
		if(flag==1){
			d=c[0];  //给栈中的各个页面权重排序，c[]最大的是要置换的那个页面 
			for(i=0;i<m;i++){
			if(d<=c[i]){
				d=c[i];
				q=i;
			}
		}
		change++;
		b[q]=a[cou];
		c[q]=0;
		for(i=0;i<m;i++){
	        printf("%d ",b[i]);
	        }
	    printf("\n");
    	}
    	cou++;
    }	
    x=(double)(change+3.00)/n;
	printf("置换的次数：%d\n",change);
	printf("缺页的数量：%d\n",change+3);
	printf("缺页率（命中率）：%.4f",x);//小数点后保留四位 
}

void OPT(int n,int m,int *a){
	//最佳置换算法OPT
	int q,temp,flag,change;//temp用于比大小赋予初值 
	double x;//x为缺页率 
    change=0;
	int *b,*c,*d; //b[3]为有3个位置的栈,a[]为要输入的页面序列
	b= (int *)malloc(m * sizeof(int));
	c= (int *)malloc(n * sizeof(int));//放置备用页面序列，和a[]一样。作为比距离远近的时候用，看那个页面在最长（未来）时间内不被访问 
	d= (int *)malloc(m * sizeof(int));//放置栈中的页面在未来第一次出现的位置 
	int i,j,cou=0;
	for(i=0;i<m;i++){
	    b[i]=a[cou];
	    cou++;
	    printf("%d ",b[i]);
	}
	printf("\n");
	while(cou<n){
		flag=1;
		for(i=0;i<m;i++){  //看看栈中有没有同样的页面
			if(b[i]==a[cou]){
				flag=0;
			}
		}
		 if(flag==0){        //如果有相同页面，不做置换 
			for(i=0;i<m;i++){
				printf("%d ",b[i]);
			}
			printf("\n");
		}
		if(flag==1){        //如果没有相同页面 
		for(i=0;i<m;i++){
			for(j=cou;j<n;j++){
				if(b[i]==c[j]){
					d[i]=j;
					break;
				}
				else{
					d[i]=INF;
				}
			}
		} 
		temp=d[0];
		for(i=0;i<m;i++){
			if(temp<=d[i]){
				temp=d[i];
				q=i;
		    	}
	    	}
	    	change++;
	    	b[q]=a[cou];
	    		for(i=0;i<m;i++){
	        printf("%d ",b[i]);
	        //printf("%d* ",d[i]);
	        }
	    printf("\n");
		}
		cou++;
	}
	x=(double)(change+3.00)/n;
	printf("置换的次数：%d\n",change);
	printf("缺页的数量：%d\n",change+3);
	printf("缺页率（命中率）：%.4f",x);//小数点后保留四位 
} 

int main(){
	int select;
	int n,m,q;
	int i,j,*a;
	printf("----------------------------------------\n");
	printf("|       页面置换算法的模拟实现         |\n");
	printf("|       1.先进先出算法(FIFO)           |\n");
	printf("|       2.最近最久未使用算法(LRU)      |\n");
	printf("|       3.最佳置换算法(OPT)            |\n");
	printf("----------------------------------------\n");
	while(1){
	printf("输入页面序列数：");
    scanf("%d",&n);
    printf("输入页面序列：");
    a= (int *)malloc(n * sizeof(int));
		for(i=0;i<n;i++){
	    scanf("%d",&a[i]);//输入要执行的页面顺序
	}
    printf("输入分块数：");
    scanf("%d",&m);
    printf("请选择：");
	scanf("%d",&select);
		switch(select){
		case 1: FIFO(n,m,a);break;
		case 2: LRU(n,m,a);break;
		case 3: OPT(n,m,a);break;
		default:printf("出错");
	   }
	}
	return 0;
}
