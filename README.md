# BaseBall-Game

-실행화면-

![image](https://user-images.githubusercontent.com/102803326/173282514-06e85df3-f559-40f5-a697-41aa630f81fb.png)

-실행코드-

import java.util.*;
import java.io.*;
public class BaseBall{
	
public static int playGame() throws IOException{
	
int x, y, z;
// 컴퓨터가 선택하는 3개의 숫자
Random r= new Random();   //난수 발생

x= Math.abs(r.nextInt() % 9) + 1;
	do{
y= Math.abs(r.nextInt() % 9) + 1;
}while(y==x);
	do{
z= Math.abs(r.nextInt() % 9) + 1;
	}while((z==x)||(z==y));

System.out.println(x +", "+ y +", "+ z); /**/

return playGame(x, y, z);
}

public static int playGame(int x, int y, int z) throws IOException{
	
int count;

int strike, ball;

int[] usr = new int[3];

int[] com = { x, y, z };

System.out.println("숫자 야구 게임");

count= 0;
	do{
count++;
	do{
System.out.println("\n카운트: "+count);

BufferedReader in= new BufferedReader(new InputStreamReader(System.in));
//콘솔 화면에서 사용자가 입력하는 데이터를 받아들이는 BuffereReader() 메소드의 객체변수 in 생성
String user;  //객쳋변수 in에 들어앴는 데이터내용을 문자형데이터로 저장할 변수 생성

System.out.print("1번째 숫자: ");

user= in.readLine(); //사용자가 입력하는 데이터를 변수 user 에 저장

usr[0]= new Integer(user).intValue();


System.out.print("2번째 숫자: ");

user= in.readLine();

usr[1]= new Integer(user).intValue();

System.out.print("3번째 숫자: ");

user= in.readLine();

usr[2]= new Integer(user).intValue();

if((usr[0]==0)||(usr[1]==0)||(usr[2]==0)){
	
System.out.println("0은 입력하지 마세요. 다시 입력해주세요.");

}else if((usr[0]>9)||(usr[1]>9)||(usr[2]>9)){
	
System.out.println("1부터 9까지의 숫자 중 하나를 입력해주세요. 다시 입력해주세요.");

}else if((usr[0]==usr[1])||(usr[1]==usr[2])||(usr[0]==usr[2])){
	
System.out.println("모두 다른 숫자를 입력해주세요. 다시 입력해주세요.");

}
}while((usr[0]==0)||(usr[1]==0)||(usr[2]==0)||
		
(usr[0]>9)||(usr[1]>9)||(usr[2]>9)||

(usr[0]==usr[1])||(usr[1]==usr[2])||(usr[0]==usr[2]));
	//모든 숫자가 1~9사이, 같은 숫자가 없는 경우에만 반복문을 빠져나옴
strike = ball = 0;

if(usr[0]==com[0]) strike++;

if(usr[1]==com[1]) strike++;

if(usr[2]==com[2]) strike++;
//usr, com 두 개의 배열이 각각 완전히 일치할 경우에만 strike 처리
if(usr[0]==com[1]) ball++;

if(usr[0]==com[2]) ball++;

if(usr[1]==com[0]) ball++;

if(usr[1]==com[2]) ball++;

if(usr[2]==com[0]) ball++;

if(usr[2]==com[1]) ball++;
//usr, com 두 개의 배열의 데이터 위치가 다른 경우에만 ball 처리
System.out.println("Strike: "+ strike +" Ball: "+ ball);
}while((strike<3)&&(count<11));  //strike < 3(게임미완성), count < 11(시도횟수 10번까지)일때 반복실행
	                             //strike =< 3 이거나 count = 11(시도횟수 11번쨰)가 되면 종료
return count;
}
public static void main(String[] args) throws IOException{
	
int result;  //결과값을 위한 변수 생성

if(args.length==3){	  //게임실행 주어진 3개인 경우, 각각 정수형으로 형변환을 통해 x, y, a 에 저장
int x= Integer.valueOf(args[0]).intValue();
int y= Integer.valueOf(args[1]).intValue();
int z= Integer.valueOf(args[2]).intValue();
//난수발생시키는 경우 즉, playGame()는 해당없음.
result= playGame(x, y, z);

}else{
result= playGame();
}

System.out.println();

if(result<=2){
	
System.out.println("참 잘했어요!"); //시도횟수가 2번 이하
}else if(result<=5){
	
System.out.println("잘했어요!"); //시도횟수가 3번부터 5번 이하
}else if(result<=9){
	
System.out.println("보통이네요!");  //
}else{
	
System.out.println("분발하세요!");
}
}

		
	}


