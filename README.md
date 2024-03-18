#include<stdio.h>
#include<ctype.h>
#include<string.h>

 char infix[100],postfix[100];
int top=-1;

void push(char c){
         infix[++top]=c;
    }
char pop(){
    return infix[top--];
}
int precedence(char c){
    switch(c){
        case '^':return 3;
        case '*':
        case '/':return 2;
        case '+':
        case '-':return 1;
        defalut:return-1; 
    }
}
 int isoperator(char c){
    return(c=='+' || c=='-' || c=='*' || c=='/' || c=='^');
 }

  void convert(){
    int i=0,j=0;
    while(infix[i]!='\0'){
         if(isalnum(infix[i])){
            postfix[j++]=infix[i++];
         }else if (infix[i]=='('){
                 push(infix[i++]);
         }else if(infix[i]==')'){
                while(infix[top]!='(')
                    postfix[j++]==pop();
                    pop();
                    i++;
                }
                else{
                    while(top>=0&&precedence(infix[top])>=precedence(infix[i]))
                        postfix[j++]=pop();
                        push(infix[i++]);
                }
    }
    while(top>=0)
         postfix[j++]=pop();
         postfix[j]='\0';
  }

   void main(){
    printf("Enter INFfix exp:");
    scanf("%s",infix);
    convert();
    printf("postfix exp:%s",postfix);
   }


   #include<stdio.h>
#include<stdlib.h>
#include<string.h>
#define MAX 100
 int s[MAX];
 int top=-1;

 void push();
 void pop();
 void display();
 void palindrome();

 int main(){
    int ch;
    while(1){
        printf("\nENTER THE CHOICE\n 1.Push\n 2.pop\n 3.display \n 4.palindrome\n");
        scanf("%d",&ch);

        switch(ch){
            case 1 : push();break;
            case 2 : pop();break;
            case 3 : display();break;
            case 4 : palindrome();break;
        }
    }
    return 0;
 }

 void push(){
    int x;

    if(top==MAX-1){
        printf("Overflow");
    }else{
    printf("Enter to push element:");
    scanf("%d",&x);
    top=top+1;
    s[top]=x;
 }
 }
  
 void pop(){
    if(top==-1){
       printf("Underflow");
    }else{
    printf("The poped element is :%d",s[top]);
    top=top-1;
 }
 }

 void display(){
    for(int i=top;i>=0;i--){
        printf("|%d|\n",s[i]);
    }
 }
  void palindrome(){

    char a[10],b[10];
    printf("Enter the str\n");
    fflush(stdin);
    gets(a);
    strcpy(b,a);
    strrev(b);
    if(strcmp(a,b)==0){
    printf("this is palindrome");
    }else{
    printf("This is not palindrome");
  }
  
   
