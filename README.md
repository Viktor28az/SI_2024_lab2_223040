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
![sliaaaaaaaa](https://github.com/Viktor28az/bonobo/assets/162887208/60c82ee8-4d3e-419e-874c-0153adda4b3a)

3.Цикломатската сложенсот може да се пресмета на три начини: 
3.1.Преку бројот на региони 
3.2.Преку бројот на врски – бројот на јазли +2 ----> V(G)= E – N +2 3.3.
Преку бројот предикатни јазли во даден граф +1.
Па според ова E=39 број на врски ; N=31 број на јазли  39-31+2=8+2=10

4
Every statement	AllItems=’ ’	Allitems=“1“; name=“ “; barcode=“-1“	Allitems=“1“; name=“ “; barcode=“1“; discount=“10“;sum=“10“ paymen=“20“	Allitems=“1“; name=“ “; barcode=“1“; discount=“-1“;sum=“30“ paymen=“20“

![image](https://github.com/Viktor28az/bonobo/assets/162887208/e3a7d023-75d3-45aa-9d2b-1d76fbb2d5a8)

