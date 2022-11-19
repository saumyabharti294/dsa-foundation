#include<bits/stdc++.h>
using namespace std;

bool check(string s)
{
    int n=s.length();
    map<char,int> m;
    for(auto i:s)
    {
        m[i]++;
    }
    int count=0;
    for(auto i=m.begin();i!=m.end();i++)
    {
        if(i->second%2)
        {
            count++;
        }
    }
    if(n%2 && count==1){
        return true;
    }
    if(!(n%2) && count==0){
        return true;
    }
    return false;
}

int main()
{
    string s1;
    cout<<"enter the string"<< endl;
    //cin >> s1;
    while(cin>>s1)
    {
    
        if(s1[0]=='0')
        {
            break;
        }
        string s;s=s1;
        int n=s.length();
        //first check if
        int count=0;
        bool initial=false;
        if(n%2){
            initial=true;
        }
        if(check(s))
        {
            for(int i=0; i<n/2; i++)
            {
                bool fl=false;
                int j=0;
                for(j=n-1-i; j>i; j--)
                {

                    if(s[j]==s[i])
                    {
                        fl=true;
                        for(int k=j;k<n-1-i;k++)
                        {
                            swap(s[k],s[k+1]);
                            count++;
//                            cout<<cnt<<endl<<flush;
                        }
//                        cout<<" "<<i<<" "<<count<<endl<<flush;
                        break;
                    }
                }
                if(!fl&&initial)
                {
                    for(int k=i;k<n/2;k++)
                    {
                        swap(s[k],s[k+1]);
                        count++;

                    }
//                    cout<<count<<" "<<i<<" "<<endl<<flush;
                }
            }
            cout<<count<<endl;
        }
        else{
            cout<<"not possible"<<endl;
        }
        cout<<"Again enter another string"<<endl;
    }

}
