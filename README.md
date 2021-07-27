# Paranthesis-Matching

#include <iostream>
#include<string.h>
using namespace std;

class Stack
{
public:
    int size;
    int top;
    char *s;
};

void push(Stack *st,char x)
{
    if(st->top==st->size-1)
    {
        cout<<"Stack Overflow"<<endl;
    }
    else
    {
        st->top++;
        st->s[st->top]=x;
    }
}

int isEmpty(Stack st)
{
    if(st.top==-1)
    {
        return 1;
    }
    else
    {
        return 0;
    }
}

char pop(Stack *st)
{
    char x=1;
    if(st->top==-1)
    {
        cout<<"Stack Underflow"<<endl;
    }
    else
    {
        x=st->s[st->top];
        st->top--;
    }
    return x;
}



int isBalance(char *exp)
{
    Stack st;
    st.size=strlen(exp);
    st.top=-1;
    st.s=new char[st.size];
    for(int i=0;exp[i]!='\0';i++)
    {
        if(exp[i]=='(')
        {
            push(&st,exp[i]);
        }
        else if(exp[i]==')')
        {
            if(isEmpty(st))
            {
                return false;
            }
            else
            {
                pop(&st);
            }
        }
    }
    if(isEmpty(st))
    {
        return true;
    }
    else
    {
        return false;
    }
}

int main()
{
    char exp[20];
    cout<<"Enter the expression: ";
    cin>>exp;
    if(isBalance(exp))
    {
        cout<<"Balanced"<<endl;
    }
    else
    {
        cout<<"Unbalanced"<<endl;
    }
    return 0;
}
