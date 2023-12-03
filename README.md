#include <stdio.h>

int getDiscountPercent(char membership_type){
	char S = 10, G = 20, P = 30, X = 0;

    bool check = false;
	float discount;

    while (!check) {
        if (membership_type == 'S' || membership_type == 's') {
            check = true;
            return 10;
        }

        else if (membership_type == 'G' || membership_type == 'g') {
            check = true;
            return 20;
        }

        else if (membership_type == 'P' || membership_type == 'p') {
            check = true;
            return 30;
        }

        else if (membership_type == 'X' || membership_type == 'x') {
            check = true;
            return 0;
        }

        else {
            printf("\n\tInvalid code , Please enter again : ");
            printf("\n\tEnter membership type (S or G or P,X for non member): ");
            scanf("%c", &membership_type);
            getchar();
        }
    }

}

int main(int argc, char *argv[])
{

    char mbrtype; float itmPrice, discount, disPrice; int numItem;


    printf("\t\t\t\tSURIA SUPERMARKET\t\t\t\n");    
	printf("\t\t\t\t\t\t\t\t\t\n");



    
    char names[3][40];
    char membershipType[3];
    float totalPurchase[3];
    float customerPayment[3];
    
    for( int i = 0 ; i < 3; i++  ) {
    	char membership_type;
    	char add_items;
    	float price;
    	float total_price = 0;
    	float amount_to_pay = 0;
    	float discount_percentage = 0;
    	float discount_amount;
    	float discounted_price;
    	int items = 1;
    	
    	printf( "Enter name : " );
    	fgets( names[i], 40, stdin ); 	
    	printf("\tEnter membership type (S or G or P,X for non member): ");
    scanf("%c", &membership_type);
    getchar();
    discount_percentage = getDiscountPercent(membership_type);
   


    	
    bool next = true;

    while (next) {
    			
		printf("\n");
		printf("\tItem %d \t\t\t\t\t\t\n", items);
        printf("\tEnter item price : RM ");
        scanf("%f", &price);
        if (discount_percentage != 0) {
            discount_amount = ((discount_percentage / 100) * price);
        }
        else {
            discount_amount = 0;
        }

        discounted_price = (price - discount_amount);
        printf("\tDiscount(%%) : %.f\t\t\t\t\t\t\t\n", discount_percentage);
        printf("\tDiscounted price : %.2f\t\t\t\t\t\t\n", discounted_price);
		


        printf("\tAdd Items (Y/N)  :");
        scanf(" %c", &add_items);
        getchar();


        if (add_items == 'Y' || add_items == 'y') {
            items+=1;
            total_price += price;
            amount_to_pay += discounted_price;
            next = true;

        }
        else if (add_items == 'N' || add_items == 'n') {
            items += 1;
            total_price += price;
            amount_to_pay += discounted_price;
            next = false;

        }
        else {
            printf("\tInvalid input , please enter again  : \t\t\t\t\t\t|\n");
        }
    }
    printf("\n");
    printf("\t***Purchase Details***\n");
    printf("\tMembership type : %c\t\t\t\t\t\t\n", membership_type);
    printf("\tDiscount(%%) : %.f\t\t\t\t\t\t\t\n", discount_percentage);
    printf("\tNumber of Items : %d \t\t\t\t\t\t\n", items-1);
    printf("\tTotal Purchase : %.2f\t\t\t\t\t\t\n", total_price);
    printf("\tAmount To Pay : %.2f\t\t\t\t\t\t\n", amount_to_pay);
    
    totalPurchase[i] = total_price ;
    customerPayment[i] = amount_to_pay;
    membershipType[i]= membership_type;
    }
	printf ("\n\nSales Summary\n"); //output statement after the looping is end
	printf ("\n===============================================================================\n");
	printf ("Customer Name\tMembership Type \tTotal Purchase(RM)\tAmount Paid(RM)");// following the output
	printf ("\n===============================================================================\n");
	for( int i = 0 ; i < 3; i++  ) {

		printf ("%s\t\t\t%c\t\t\t%.2f\t\t%.2f\t\n",names[i],membershipType[i],totalPurchase[i],customerPayment[i]);//simple version
  	}
     
    return 0;
}
