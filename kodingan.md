#include <stdio.h>
#include <stdlib.h>
#include<conio.h>
#define MAX 3

typedef struct {
    int data[MAX];
    int head;
    int tail;
}Queue;

Queue antri;

int Kosong ()
{
    if(antri.tail==-1)
    {
        return 1;
    }
    return 0;
}

int Penuh()
{
    if(antri.tail==MAX-1)
    {
        return 1;
    }
    return 0;
}

void Enqueue(int data)
{
    if(Kosong()==1)
    {
        antri.head = antri.tail = 0;
        antri.data[antri.tail] = data;
        printf("%d masuk", antri.data[antri.tail]);
        //void Tampil()
        //{
            if(Kosong()==0)
            {
                for(int i=antri.head; i<=antri.tail; i++)
                {
                    printf("%d ", antri.data[i]);
                }
            } else
            {
                printf("Antrian Kosong!");
            }
        //}*/
    }else if (Penuh()==0)
    {
        antri.tail++;
        antri.data[antri.tail] = data;
        printf("%d masuk", antri.data[antri.tail]);
    }

}

int Dequeue()
{
   int d = antri.data[antri.head];
   for(int i=antri.head; i<=antri.tail-1; i++)
   {
       antri.data[i] = antri.data[i+1];
   }
   antri.tail--;
   return d;
}



void Awal()
{
    antri.head = antri.tail = -1;
}

void Display()
{
    if(Kosong()==0)
            {
                for(int i=antri.head; i<=antri.tail; i++)
                {
                    printf("%d ", antri.data[i]);
                }
            }else
            {
                printf("Antrian Kosong!");
            }
}

void Destroy()
{
    antri.head = antri.tail = -1;
    printf("Data Telah Dibersihkan!!");
}
int main()
{
    int pilih;
    int data;
    Awal();
    do
    {
        printf("\n\n");
        printf("1. Enqueue\n");
        printf("2. DEqueue\n");
        printf("3. Display\n");
        printf("4. Destroy\n");
        printf("5. Keluar\n");
        printf("\nMasukan pilihan anda = ");
        scanf("%d", &pilih);\
        switch(pilih)
        {
        case 1:
            system("cls");
            printf("Data = ");
            scanf("%d", &data);
            Enqueue(data);
            getch();
        break;
        case 2:
             system("cls");
            printf("Data yang keluar : %d", Dequeue());
            getch();
        break;
        case 3:
             system("cls");
            Display();
            getch();
        break;
        case 4:
            Destroy();
            system("cls");
            getch();
        break;
        case 5:
            system("cls");
            getch();
            printf("Terima Kasih :)");
            exit(0);
        break;
        default:
            printf("Pilihan tidak ada !!");

        }
    }while(pilih!=5);
}
