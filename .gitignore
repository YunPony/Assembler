import java.util.*;
import java.io.*;
class pony{
	static HashMap<String, Integer> map = new HashMap<String, Integer>();
	static int locctr,location;
	static String Opcode;
	static String[] Op = new String[]{"ADD","AND","COMP","DIV","J","JEQ","JGT","JLT", "JSUB", "LDA", "LDCH", "LDL", "LDX", "MUL", "OR", "RD", "RSUB", "STA", "STCH", "STL", "STX", "SUB", "TD", "TIO", "TIX", "WD" };
	static Scanner opt;
		public static void main(String args[])
		{
			try
			{
				opt = new Scanner(new File("test.txt"));
			}catch(Exception e){System.out.println(e.getMessage());}
			while(true){
		
				String optp=opt.nextLine();//1
				String opotpt[] = optp.split("\t");
				
				if(opotpt[1].equals("START")){
					locctr=Integer.parseInt(opotpt[2],16);
					location = locctr;
					}
				if(opotpt[1].equals("END")){
					break;
					}
				if(opotpt[1].equals("WORD")){
					locctr+=Integer.parseInt(opotpt[2]);
					location = locctr+3;
					
				}
				if(opotpt[1].equals("BYTE")){
					locctr+=opotpt[2].length()-3;
					location = locctr;
					
				}
				if(opotpt[1].equals("RESB")){
					locctr+=Integer.parseInt(opotpt[2]);
					location = locctr+3;
					
				}
				if(opotpt[2].equals("RESW")){
					locctr+=Integer.parseInt(opotpt[2]);
					location = locctr+3;
					
				}
				if(!opotpt[0].equals(" ")&&!opotpt[0].equals("")){
					map.put(opotpt[0],new Integer(location));				
				}
			}
			try//2
			{
				opt = new Scanner(new File("test.txt"));
			}catch(Exception e){System.out.println(e.getMessage());}
			while(true){
				String optp=opt.nextLine();
				String opotpt[] = optp.split("\t");
				if(opotpt[1].equals("END"))
				{
					break;
				}
				String ans = "";
				switch(opotpt[1]){
					case "LDA":
						ans+="00";
						String arr_cut[]=opotpt[2].split(",");
						int tmp = 0;
						for(String str : arr_cut)
							if(!str.equals("X"))
								tmp += Integer.parseInt(str,16);
							else
								tmp += 32768;
						ans += Integer.toString(tmp,16);
						break;
					case "STA":
						ans+="0C";
						ans+=Integer.toString(map.get(opotpt[2]),16);
						break;
					case "RSUB":
						ans+="1C";
						break;
					case "SUB":
						ans+="4C0000";
						break;
					case "J":
						ans += "3c"+Integer.toString(map.get(opotpt[2]),16);
						break;
				}
				System.out.println(opotpt[0]+"\t"+opotpt[1]+"\t"+opotpt[2]+"\t"+ans);
			}
		}
		
}
