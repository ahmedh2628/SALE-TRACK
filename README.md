#include <iostream>  
#include <string>
using namespace std;

int main()
{
    cout << "WELCOME TO SALE-TRACK:" << endl;

    string user;
    int passcode;
    double products[10] = { 26, 34, 54, 13, 28 };                      //quantity of already declared products
    double chair = products[2], table = products[3], bed = products[4];
    double dresser = products[0], mirror = products[1];           //already declared products
   
    //we can also add products ,i've added only 1 for example.
    
    int newproduct;                                    //FOR ADDING NEW PRODUCT IN INVENTORY
    string prodname = ""; 
    double totalSales = 0;         //for calculating total sales
    string productsold = "";        // sold products
    //items owned rates
    double own[5]{ 50,65,120,70,40 };
    double chairown = own[0];
    double tableown = own[1];
    double bedown = own[2];
    double dresserown = own[3];
    double mirrorown = own[4];

    //fixed sale prices
    double saleprice[5]{ 55,70,125,80,50 };
    double chairprice = saleprice[0];
    double tableprice = saleprice[1];
    double bedprice = saleprice[2];
    double dresserprice = saleprice[3];
    double mirrorprice = saleprice[4];

    double newprodown;    //owned price of new product that user can add
    double newprodprice;    //sale price of product that a user can add

    double revenew;                                           //FOR REVENEW,TOTAL COST AND PROFIT
    double totalcost;
    double profit;

    double totalcart = 0;                       //for clients cart

    do {                                      //this loop will run after completing first query.
        cout << "ADMIN or CLIENT: ";

        cin >> user;
    

        if (user == "admin")                                    //FOR ADMIN
        {
            cout << "ENTER PASSWORD: ";
            cin >> passcode;

            if (passcode != 1234) {
                cout << "ENTER CORRECT PASSWORD" << endl; // WRONG PASSCODE SYSTEM EXITS
                return 0;
            }

            double choice;
            do {             // loop is for giving options to admin after completing any operation.
                cout << "---------------------------------------------------------------" << endl;
                cout << "1.ADD NEW PRODUCT" << endl;
                cout << "2.MANAGE-SALES" << endl;
                cout << "3.INVENTORY" << endl;
                cout << "4.TOTAL SALES" << endl;
                cout << "5.PROFIT MANAGER" << endl;
                cout << "0.EXIT" << endl;
                cout << "---------------------------------------------------------------" << endl;
                cout << "ENTER YOUR CHOICE: ";
                cin >> choice;
                cout << "---------------------------------------------------------------" << endl;

                if (choice == 1)                                   // ADDING NEW PRODUCT
                {
                    cout << "ADD NEW PRODUCT: " << endl;
                    cout << "PRODUCTS:" << endl;
                    cout << "1. Chair" << endl;
                    cout << "2. Table" << endl;
                    cout << "3. Bed" << endl;
                    cout << "4. Dresser" << endl;
                    cout << "5. Mirror" << endl;
                    cout << "6.Add new Product:" << endl;
                    cout << "---------------------------------------------------------------" << endl;
                    cout << "ENTER YOUR CHOICE: ";
                    int add, pick;                  //declaration for adding products and choosing which to add.

                    cin >> pick;
                    cout << "---------------------------------------------------------------" << endl;

                    switch (pick)
                    {
                    case 1:
                        cout << "CHAIRS IN STOCK: " << chair << endl;
                        cout << "NEW CHAIRS: ";
                        cin >> add;
                        chair = chair + add;
                        cout << "TOTAL CHAIRS: " << chair << endl;
                        break;
                    case 2:
                        cout << "TABLES IN STOCK: " << table << endl;
                        cout << "NEW TABLES: ";
                        cin >> add;
                        table = table + add;
                        cout << "TOTAL TABLES: " << table << endl;
                        break;
                    case 3:
                        cout << "BEDS IN STOCK: " << bed << endl;
                        cout << "NEW BEDS: ";
                        cin >> add;
                        bed = bed + add;
                        cout << "TOTAL BEDS: " << bed << endl;
                        break;
                    case 4:
                        cout << "DRESSERS IN STOCK: " << dresser << endl;
                        cout << "NEW DRESSERS: ";
                        cin >> add;
                        dresser = dresser + add;
                        cout << "TOTAL DRESSERS: " << dresser << endl;
                        break;
                    case 5:
                        cout << "MIRRORS IN STOCK: " << mirror << endl;
                        cout << "NEW MIRRORS: ";
                        cin >> add;
                        mirror = mirror + add;
                        cout << "TOTAL MIRRORS: " << mirror << endl;
                        break;
                    case 6:
                        cout << "ADDING NEW PRODUCT IN STOCK:" << endl;
                        cout << "PRODUCT NAME: ";
                        cin >> prodname;
                        cout << "QUANTITY OF " << prodname << ": ";
                        cin >> newproduct;
                        cout << prodname << "OWNED PRICE: ";
                        cin >> newprodown;
                        cout << prodname << "SALE PRICE: ";
                        cin >> newprodprice;

                        break;
                    default:
                        cout << "Invalid choice!" << endl;
                        break;
                    }
                }
                else if (choice == 2)                                   //FOR SALES MANAGEMENT
                {
                    cout << "SALES MANAGER" << endl;
                    cout << "PRODUCTS:" << endl;
                    cout << "1. Chair" << endl;
                    cout << "2. Table" << endl;
                    cout << "3. Bed" << endl;
                    cout << "4. Dresser" << endl;
                    cout << "5. Mirror" << endl;
                    cout << "6." << prodname << endl;

                    cout << "---------------------------------------------------------------" << endl;
                    cout << "ENTER YOUR CHOICE: ";
                    int sale, choose;       //declaration for sold products and choosing which is sold.
                    cin >> choose;
                    cout << "---------------------------------------------------------------" << endl;

                    switch (choose)
                    {
                    case 1:
                        cout << "CHAIRS IN STOCK: " << chair << endl;
                        cout << "SOLD CHAIRS: ";
                        cin >> sale;
                        chair = chair - sale;
                        totalSales = totalSales + sale;
                        productsold = productsold + "Chair: " + to_string(sale) + " sold\n";
                        revenew = totalSales * chairprice;                                   //FINDS REVENEW
                        totalcost = totalSales * chairown;                                  //FINDS TOTAL COST
                        profit = revenew - totalcost;                                    //SUBTRACT/S COST FROM REVENEW AND DECLARES PROFIT
                        cout << "CHAIRS REMAINING: " << chair << endl;
                        break;
                    case 2:
                        cout << "TABLES IN STOCK: " << table << endl;
                        cout << "SOLD TABLES: ";
                        cin >> sale;
                        table = table - sale;
                        totalSales = totalSales + sale;
                        productsold = productsold + "Table: " + to_string(sale) + " sold\n";
                        revenew = totalSales * tableprice;                 //FINDS REVENEW
                        totalcost = totalSales * tableown;  //FINDS TOTAL COST

                        profit = revenew - totalcost;                            //SUBTRACT/S COST FROM REVENEW AND DECLARES PROFIT

                        cout << "TABLES REMAINING: " << table << endl;
                        break;
                    case 3:
                        cout << "BEDS IN STOCK: " << bed << endl;
                        cout << "SOLD BEDS: ";
                        cin >> sale;
                        bed = bed - sale;
                        totalSales = totalSales + sale;
                        productsold = productsold + "Bed: " + to_string(sale) + " sold\n";
                        revenew = totalSales * bedprice;                //FINDS REVENEW
                        totalcost = totalSales * bedown;//FINDS TOTAL COST
                        profit = revenew - totalcost;                         //SUBTRACT/S COST FROM REVENEW AND DECLARES PROFIT

                        cout << "BEDS REMAINING: " << bed << endl;
                        break;
                    case 4:
                        cout << "DRESSERS IN STOCK: " << dresser << endl;
                        cout << "SOLD DRESSERS: ";
                        cin >> sale;
                        dresser = dresser - sale;
                        totalSales = totalSales + sale;
                        productsold = productsold + "Dresser: " + to_string(sale) + " sold\n";
                        revenew = totalSales * dresserprice;         //FINDS REVENEW
                        totalcost = totalSales * dresserown;                //FINDS TOTAL COST
                        profit = revenew - totalcost;                  //SUBTRACT/S COST FROM REVENEW AND DECLARES PROFIT

                        cout << "DRESSERS REMAINING: " << dresser << endl;
                        break;
                    case 5:
                        cout << "MIRRORS IN STOCK: " << mirror << endl;
                        cout << "SOLD MIRRORS: ";
                        cin >> sale;
                        mirror = mirror - sale;
                        totalSales = totalSales + sale;
                        productsold = productsold + "Mirror: " + to_string(sale) + " sold\n";
                        revenew = totalSales * mirrorprice;           //FINDS REVENEW
                        totalcost = totalSales * mirrorown;                           //FINDS TOTAL COST
                        profit = revenew - totalcost;                    //SUBTRACT/S COST FROM REVENEW AND DECLARES PROFIT
                        cout << "MIRRORS REMAINING: " << mirror << endl;
                        break;
                    case 6:
                        cout << prodname << "in stock: " << newproduct << endl;
                        cout << "Sold " << prodname << ": ";
                        cin >> sale;

                        newproduct = newproduct - sale;
                        totalSales = totalSales + sale;

                        productsold = productsold + prodname;

                        productsold += " " + to_string(sale) + "  sold\n";
                        revenew = totalSales * newprodprice;               //FINDS REVENEW
                        totalcost = totalSales * newprodown;                         //FINDS TOTAL COST
                        profit = revenew - totalcost;                //SUBTRACT/S COST FROM REVENEW AND DECLARES PROFIT

                        cout << prodname << "remaining: " << newproduct << endl;
                        break;
                    default:
                        cout << "Invalid choice!" << endl;
                        break;
                    }
                }
                else if (choice == 3)                            //INVENTORY
                {
                    cout << "YOUR INVENTORY:" << endl;
                    cout << "CHAIRS: " << chair << endl;
                    cout << "TABLES: " << table << endl;
                    cout << "BEDS: " << bed << endl;
                    cout << "DRESSERS: " << dresser << endl;
                    cout << "MIRRORS: " << mirror << endl;
                    cout << prodname << ": " << newproduct << endl;
                }
                else if (choice == 4)                                           //TOTAL SALES
                {
                    cout << "TOTAL SALES: " << totalSales << endl;
                    cout << "SALES DETAILS:  " << endl;
                    cout << productsold << endl;
                }
                else if (choice == 5)                                                          //PROFIT MANAGER
                {
                    cout << "PROFIT MANAGER: " << endl;
                    cout << " " << endl;
                    cout << "SALES DETAILS:  " << endl;
                    cout << productsold << endl;
                    cout << "TOTAL REVENEW: " << revenew << "$" << endl;                    //TOTAL REVENEW
                    cout << "TOTAL PROFIT: " << profit << "$" << endl;          //TOTAL PROFIT

                }
            } while (choice != 0);
        }
        else if (user == "client")                              //FOR CLIENT
        {
            cout << "ENTER PASSWORD: ";
            cin >> passcode;

            if (passcode != 1234) {
                cout << "ENTER CORRECT PASSWORD" << endl;           //WRONG PASSCODE SYSTEM EXITS
                return 0;
            }
            double choose;
            do {

                cout << " " << endl;
                cout << "---------------------------------------------------------------" << endl;

                cout << "1.INVENTORY" << endl;
                cout << "2.PRICE LIST" << endl;
                cout << "3.CART" << endl;


                cout << "0.EXIT" << endl;
                cout << "---------------------------------------------------------------" << endl;           //a
                cout << "ENTER YOUR CHOICE: ";
                cin >> choose;
                cout << "---------------------------------------------------------------" << endl;         //h
                                                                                                                 //m
                cout << " " << endl;                                                                  //e
                if (choose == 1)                                                                                     //d
                {
                    cout << "YOUR INVENTORY:" << endl;
                    cout << "CHAIRS: " << chair << endl;
                    cout << "TABLES: " << table << endl;
                    cout << "BEDS: " << bed << endl;
                    cout << "DRESSERS: " << dresser << endl;
                    cout << "MIRRORS: " << mirror << endl;
                    cout << prodname << ": " << newproduct << endl;
                }
                else if (choose == 2)
                {
                    cout << "1.CHAIR:" << chairprice << "$" << endl;
                    cout << "2.TABLE:" << tableprice << "$" << endl;
                    cout << "3.BED:" << bedprice << "$" << endl;
                    cout << "4.DRESSER:" << dresserprice << "$" << endl;
                    cout << "5.MIRROR:" << mirrorprice << "$" << endl;


                }
                else if (choose == 3)
                {
                    int itemChoice, quantity;       //decleration for item choosing and quantity to buy
                    double itemTotal = 0;
                    cout << "Select an item to add to cart: " << endl;
                    cout << "1. Chair" << endl;
                    cout << "2. Table" << endl;
                    cout << "3. Bed" << endl;
                    cout << "4. Dresser" << endl;
                    cout << "5. Mirror" << endl;
                    cout << "Enter your choice: ";
                    cin >> itemChoice;

                    cout << "Enter quantity: ";
                    cin >> quantity;

                    // Add item to cart and calculate total cost
                    if (itemChoice == 1 && chair >= quantity) {
                        totalcart = totalcart + chairprice * quantity;
                        cout << quantity << " Chairs added to cart." << endl;
                    }
                    else if (itemChoice == 2 && table >= quantity) {
                        totalcart = totalcart + tableprice * quantity;
                        cout << quantity << " Tables added to cart." << endl;
                    }
                    else if (itemChoice == 3 && bed >= quantity) {
                        totalcart = totalcart + bedprice * quantity;
                        cout << quantity << " Beds added to cart." << endl;
                    }
                    else if (itemChoice == 4 && dresser >= quantity) {
                        totalcart = totalcart + dresserprice * quantity;
                        cout << quantity << " Dressers added to cart." << endl;
                    }
                    else if (itemChoice == 5 && mirror >= quantity) {
                        totalcart = totalcart + mirrorprice * quantity;
                        cout << quantity << " Mirrors added to cart." << endl;
                    }
                    else {
                        cout << "Not enough stock available." << endl;
                    }

                    cout << "Total cart value: $" << totalcart << endl;



                }


            } while (choose != 0);

        }

    } while (user != "exit");    //end of first loop if user enters exit it will end

    return 0;
}
