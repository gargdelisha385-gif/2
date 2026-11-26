# 2
#include <stdio.h>

float balance = 10000;
int pin = 1234;

// Function for Balance Enquiry
void balanceEnquiry()
{
    printf("\nYour available balance is: Rs. %.2f\n", balance);
}

// Function for Cash Withdrawal
void cashWithdrawal()
{
    float amount;

    printf("\nEnter amount to withdraw: ");
    scanf("%f", &amount);

    if(amount > 0 && amount <= balance)
    {
        balance = balance - amount;

        printf("Please collect your cash.\n");
        printf("Remaining balance: Rs. %.2f\n", balance);
    }
    else
    {
        printf("Insufficient balance or invalid amount!\n");
    }
}

// Function for Cash Deposit
void cashDeposit()
{
    float amount;

    printf("\nEnter amount to deposit: ");
    scanf("%f", &amount);

    if(amount > 0)
    {
        balance = balance + amount;

        printf("Amount deposited successfully!\n");
        printf("Updated balance: Rs. %.2f\n", balance);
    }
    else
    {
        printf("Invalid deposit amount!\n");
    }
}

// Function for PIN Change
void changePIN()
{
    int newPin;

    printf("\nEnter your new 4-digit PIN: ");
    scanf("%d", &newPin);

    if(newPin >= 1000 && newPin <= 9999)
    {
        pin = newPin;
        printf("PIN changed successfully!\n");
    }
    else
    {
        printf("Please enter a valid 4-digit PIN!\n");
    }
}

int main()
{
    int enteredPin;
    int choice;

    printf("===== WELCOME TO ATM =====\n");

    // PIN Verification
    for(;;)
    {
        printf("\nEnter your 4-digit PIN: ");
        scanf("%d", &enteredPin);

        if(enteredPin == pin)
        {
            printf("PIN verified successfully!\n");
            break;
        }
        else
        {
            printf("Sorry! Wrong PIN. Try again.\n");
        }
    }

    // ATM Main Menu
    for(;;)
    {
        printf("\n===== ATM MAIN MENU =====\n");

        printf("1. Balance Enquiry\n");
        printf("2. Cash Withdrawal\n");
        printf("3. Cash Deposit\n");
        printf("4. Change PIN\n");
        printf("5. Exit\n");

        printf("\nEnter your choice: ");
        scanf("%d", &choice);

        switch(choice)
        {
            case 1:
                balanceEnquiry();
                break;

            case 2:
                cashWithdrawal();
                break;

            case 3:
                cashDeposit();
                break;

            case 4:
                changePIN();
                break;

            case 5:
                printf("\nThank you for using ATM!\n");
                return 0;

            default:
                printf("\nInvalid choice! Please try again.\n");
        }
    }

    return 0;
}