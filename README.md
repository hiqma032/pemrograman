# pemrograman
package greedyproject;

import java.util.Scanner;

public class Greedyproject {
    public static void main(String[] args) {
        Greedyproject greed = new Greedyproject();
        Scanner input = new Scanner(System.in);
        int uang;
        System.out.print("== PROGRAM TUKAR KOIN ==");
        System.out.print("Masukkan nominal : ");
            uang = input.nextInt();
            if (uang > 2000){
                System.out.println("Salah input. Nominal maks Rp.2000");
            }
            else if (uang <= 2000) {
                greed.tukar(uang);
            }
    }

    int[] jenisPecah;
    int[] jmlPecah;
    int jmlAwal;
    int sisa;

    public Greedyproject(int[] jns) {
        jenisPecah = jns;
        jmlPecah = new int[jns.length];
    }

    public Greedyproject() {
        jenisPecah = new int[]{100, 200, 500};
        jmlPecah = new int[3];
    }

    private int[] tukar(int jml) {
        jmlAwal = jml;
        int i = jenisPecah.length-1;
        do{
            jmlPecah[i] = jml/jenisPecah[i];
            jml -= jmlPecah[i]*jenisPecah[i];
            i--;
        }
        while(i >= 0);
        sisa = jml;
        show();
        return jmlPecah;
    }

    private void show() {
        System.out.println("Nilai awal  : "+jmlAwal);
        System.out.println("Nilai sisa  : "+sisa);
        System.out.println("Nilai pecah : ");
        for (int i = 0; i < jenisPecah.length; i++) {
            System.out.println("Pecahan "+jenisPecah[i]+" = "+jmlPecah[i]);
        }
        System.out.println();
    }
}
