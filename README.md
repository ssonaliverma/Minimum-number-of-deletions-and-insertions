# Minimum-number-of-deletions-and-insertions

int  solve2(string x,string y)
    {
        vector<vector<int>>dp(x.size()+1,vector<int>(y.size()+1,-1));
        
        for(int i=0;i<dp[0].size();i++) dp[0][i]=0;
        for(int i=0;i<dp.size();i++) dp[i][0]=0;
        
        for(int i=1; i<dp.size();i++)
        {
            for(int j=1;j<dp[0].size();j++)
            {
                if(x[i-1]==y[j-1])
                {
                    dp[i][j]=1+dp[i-1][j-1];
                }
                else
                {
                    dp[i][j]=max(dp[i][j-1] , dp[i-1][j]);
                }
            }
        }
        
        return dp[x.size()][y.size()];
    }
        
	int minOperations(string str1, string str2) 
	{ 
	    int a=solve2(str1,str2);
	    
	    return (str2.size()-a)+(str1.size()-a);
	    
	    
	    // Your code goes here
	    
	} 
