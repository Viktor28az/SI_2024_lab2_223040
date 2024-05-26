1.Пред да се направи Control Flow Graph, потребно е во самата функција да се дефинираат сите statement-и кои ги имамме: 




public class SILab2 {
    public static boolean checkCart(List<Item> allItems, int payment){//1
        if (allItems == null){//2
            throw new RuntimeException("allItems list can't be null!");//3
        }

        float sum = 0;//4

        for (int i = 0; i < allItems.size(); i++){//5
            Item item = allItems.get(i);//6
            if (item.getName() == null || item.getName().length() == 0){//7
                item.setName("unknown");//8
            }
            if (item.getBarcode() != null){//9
                String allowed = "0123456789";//10
                char chars[] = item.getBarcode().toCharArray();//11
                for (int j = 0; j < item.getBarcode().length(); j++){//12
                    char c = item.getBarcode().charAt(j);//13
                    if (allowed.indexOf(c) == -1){//14
                        throw new RuntimeException("Invalid character in item barcode!");//15
                    }
                }
                if (item.getDiscount() > 0){//16
                    sum += item.getPrice()*item.getDiscount();//17
                }
                else {
                    sum += item.getPrice();//18
                }
            }//19
            else {
                throw new RuntimeException("No barcode!");//20
            }
            if (item.getPrice() > 300 && item.getDiscount() > 0 && item.getBarcode().charAt(0) == '0'){//21
                sum -= 30;//22
            }
        }//5.3
        if (sum <= payment){//23
            return true;//24
        }
        else {
            return false;//25
        }
    }//26
}

2
![screencapture-app-diagrams-net-2024-05-26-22_07_29](https://github.com/Viktor28az/SI_2024_lab2_223040/assets/162887208/88d53fac-0d9b-4e59-9e89-08e143e13c80)



3.Цикломатската сложенсот може да се пресмета на три начини: 
3.1.Преку бројот на региони 
3.2.Преку бројот на врски – бројот на јазли +2 ----> V(G)= E – N +2 3.3.
Преку бројот предикатни јазли во даден граф +1.
Па според ова E=38 број на врски ; N=30 број на јазли  38-30+2=8+2=10

4


![image](https://github.com/Viktor28az/bonobo/assets/162887208/bc51a8a7-3cf5-44a3-aa2f-d4ff8bea2a3e)



			
![image](https://github.com/Viktor28az/bonobo/assets/162887208/0f319f4c-c6fb-484f-a661-17ad20ade391)


6
![image](https://github.com/Viktor28az/bonobo/assets/162887208/7a9157bc-b4db-4228-a2f3-815a1094d098)

![image](https://github.com/Viktor28az/SI_2024_lab2_223040/assets/162887208/85e4764b-c330-4b27-81f3-b1fc3f5ae81a)


