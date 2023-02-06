# virus
# c
신종 바이러스인 웜 바이러스는 네트워크를 통해 전파된다. 첫째 줄에는 컴퓨터의 수가 주어진다. 컴퓨터의 수는 100 이하이고 각 컴퓨터에는 1번 부터 차례대로 번호가 매겨진다. 둘째 줄에는 네트워크로 연결된 수가 주어진다. 이어서 그 수만큼 한 줄에 한 쌍씩 네트워크 상에서 직접 연결되어 있는 컴퓨터의 번호 쌍이 주어진다. 1번 컴퓨터를 통해 웜 바이러스에 걸리게 되는 컴퓨터의 수를 출력하는 프로그램을 작성해보자!

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int computer[100][100];
int network[100];
int cnt=0;
void dfs(int t,int n);


void dfs(int t,int n){
	int i;
	network[t]=1;
	cnt++;
	for(i=0;i<n;i++){
		if(network[i]==0 && computer[t][i]==1){ 
			dfs(i,n);}}
	return;
}


int main(){
	int n,m,j,a,b;
	scanf("%d",&n);
	scanf("%d",&m);
	for(j=0;j<m;j++){
		scanf("%d %d",&a,&b);  
		computer[a][b]=1; //연결된 컴퓨터사이를 1로 표시  
		computer[b][a]=1;}
	dfs(1,n);
	printf("바이러스 걸린 컴퓨터의 수: %d",cnt-1); //컴퓨터1을 빼고 나머지들  
	return 0;
}
