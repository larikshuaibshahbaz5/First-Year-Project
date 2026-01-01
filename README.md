# First-Year-Project
A console-based Hospital Management System developed in C language. This project allows users to manage hospital operations such as adding and removing doctors, nurses, staff, and patients. It also supports patient discharge and doctor appointment selection through a menu-driven interface. 

#include<stdio.h>
#include<conio.h>
#include<string.h>

// *Arrays for naming of variable
   char doctor[10][20];
   char nurse[10][20];
   char staff[10][20];
   char patient[10][20];
   
// *Counters*
   int dCount = 0, sCount = 0, nCount = 0, pCount = 0;
   
// *Funtion Decelaration* 
   void manager();
   void addpatient();
   void dischargepatient();
   void appointment();
   void about_hospital();
   
   int main(){
   	int choice;
    do{
		
   	printf("======= Hospital App =======\n");
   	printf("1. Manager Login\n");
   	printf("2. Add Patient\n");
   	printf("3. Discharge Patient\n");
   	printf("4. Appointment to Doctor\n");
   	printf("5. About Hospital\n");
   	printf("6. Exit\n");
   	printf("--------------------------\n");
   	
   	printf("Enter Your Choice\n");
   	scanf("%d",&choice);
   	
   	switch(choice){
   	case 1: manager(); break;
   	case 2: addpatient(); break;
   	case 3: dischargepatient(); break;
   	case 4: appointment(); break;
   	case 5: about_hospital(); break;
   	case 6: printf("Exiting......"); break;
   	default: printf("Invalid choice");
   }
   }while(choice != 6);
   	return 0;
   }
// *Function Defination*
// *Manager*
void manager(){
    int pass, ch, option, id, i;

    printf("Enter The Manager Password: ");
    scanf("%d", &pass);

    if(pass != 12345){
        printf("Wrong Password!\n");
        return;
    }

    do{
        printf("\n===== MANAGER MENU =====\n");
        printf("1. Add Doctor\n");
        printf("2. Fire Doctor\n");
        printf("3. Add Nurse\n");
        printf("4. Fire Nurse\n");
        printf("5. Add Other Staff\n");
        printf("6. Fire Other Staff\n");
        printf("7. Back\n");
        printf("Enter choice: ");
        scanf("%d", &ch);

        // *ADD DOCTOR* 
        if(ch == 1){
            if(dCount >= 10){
                printf("Doctor limit reached!\n");
            } else {
                printf("Enter Doctor Name: ");
                scanf("%s", doctor[dCount]);
                dCount++;
                printf("Doctor Added | ID = %d\n", dCount);
            }
        }

        // *FIRE DOCTOR*
        else if(ch == 2){
            if(dCount == 0){
                printf("No doctors to fire.\n");
                continue;
            }

            printf("1. Fire One Doctor\n");
            printf("2. Fire All Doctors\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nDoctor List:\n");
                for(i = 0; i < dCount; i++)
                    printf("ID %d | %s\n", i+1, doctor[i]);

                printf("Enter Doctor ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > dCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < dCount-1; i++)
                        strcpy(doctor[i], doctor[i+1]);
                    dCount--;
                    printf("Doctor Fired Successfully!\n");
                }
            }
            else if(option == 2){
                dCount = 0;
                printf("All Doctors Fired!\n");
            }
        }

        // *ADD NURSE*
        else if(ch == 3){
            if(nCount >= 10){
                printf("Nurse limit reached!\n");
            } else {
                printf("Enter Nurse Name: ");
                scanf("%s", nurse[nCount]);
                nCount++;
                printf("Nurse Added | ID = %d\n", nCount);
            }
        }

        // *FIRE NURSE*
        else if(ch == 4){
            if(nCount == 0){
                printf("No nurses to fire.\n");
                continue;
            }

            printf("1. Fire One Nurse\n");
            printf("2. Fire All Nurses\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nNurse List:\n");
                for(i = 0; i < nCount; i++)
                    printf("ID %d | %s\n", i+1, nurse[i]);

                printf("Enter Nurse ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > nCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < nCount-1; i++)
                        strcpy(nurse[i], nurse[i+1]);
                    nCount--;
                    printf("Nurse Fired Successfully!\n");
                }
            }
            else if(option == 2){
                nCount = 0;
                printf("All Nurses Fired!\n");
            }
        }

        // *ADD STAFF*
        else if(ch == 5){
            if(sCount >= 10){
                printf("Staff limit reached!\n");
            } else {
                printf("Enter Staff Name: ");
                scanf("%s", staff[sCount]);
                sCount++;
                printf("Staff Added | ID = %d\n", sCount);
            }
        }

        // *FIRE STAFF*
        else if(ch == 6){
            if(sCount == 0){
                printf("No staff to fire.\n");
                continue;
            }

            printf("1. Fire One Staff\n");
            printf("2. Fire All Staff\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nStaff List:\n");
                for(i = 0; i < sCount; i++)
                    printf("ID %d | %s\n", i+1, staff[i]);

                printf("Enter Staff ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > sCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < sCount-1; i++)
                        strcpy(staff[i], staff[i+1]);
                    sCount--;
                    printf("Staff Fired Successfully!\n");
                }
            }
            else if(option == 2){
                sCount = 0;
                printf("All Staff Fired!\n");
            }
        }

    } while(ch != 7);
}

   
//  *Addpatient*
void addpatient(){
	printf("\nEnter Your Patient Name : ");
	scanf("%s",&patient[pCount]);
	pCount++;
	printf("\n Patient is add | ID = %d\n",pCount);
	
}

//  *Dischargepatient*
void dischargepatient(){
	int i ,id;
	if(pCount==0){
		printf("No patient to discharge.\n");
		return;
	}
    printf("Patient List\n");
    for(i=0;i<pCount;i++){
    	printf("ID %d | %s\n",i+1,patient[i]);
	}
	printf("Enter Pateint ID to dischargepatient \n");
	scanf("%d",&id);
	if(id<1 || id>pCount){
		printf("invalid patient ID.\n");
		return;
	}
	 
	 for(i = id - 1; i < pCount - 1; i++) {
        strcpy(patient[i], patient[i + 1]);
    }

    pCount--;
    printf("Patient Discharged Successfully!\n");
}

//  *Appointment*
void appointment(){
	int i,did;
	if(dCount==0){
		printf("No doctor are avalible\n");
	} 
	else {
	printf("Avalible doctors are\n");
		for(i=0;i<dCount;i++){
			printf("ID %d | %s\n",i+1,doctor[i]);
		}
	}
	printf("Enter doctor ID for appointment \n");
	scanf("%d",&did);
	if(did<1 || did >dCount){
		printf("Invalid doctor ID \n");
		return;
	}
}

//  *About_hospital*
void about_hospital(){
	int i;
	printf("===== Hospital Staff =====\n");
	printf("Avalible doctors\n");
	for(i=0;i<dCount;i++){
		printf("ID %d | %s\n",i+1,doctor[i]);
	}
	printf("Avalible nurses\n");
	for(i=0;i<nCount;i++){
		printf("ID %d | %s\n",i+1,nurse[i]);
	}
	printf("Other staff\n");
	for(i=0;i<sCount;i++){
		printf("ID %d | %s\n",i+1,staff[i]);
	}
}
#include<stdio.h>
#include<conio.h>
#include<string.h>

// *Arrays for naming of variable
   char doctor[10][20];
   char nurse[10][20];
   char staff[10][20];
   char patient[10][20];
   
// *Counters*
   int dCount = 0, sCount = 0, nCount = 0, pCount = 0;
   
// *Funtion Decelaration* 
   void manager();
   void addpatient();
   void dischargepatient();
   void appointment();
   void about_hospital();
   
   int main(){
   	int choice;
    do{
		
   	printf("======= Hospital App =======\n");
   	printf("1. Manager Login\n");
   	printf("2. Add Patient\n");
   	printf("3. Discharge Patient\n");
   	printf("4. Appointment to Doctor\n");
   	printf("5. About Hospital\n");
   	printf("6. Exit\n");
   	printf("--------------------------\n");
   	
   	printf("Enter Your Choice\n");
   	scanf("%d",&choice);
   	
   	switch(choice){
   	case 1: manager(); break;
   	case 2: addpatient(); break;
   	case 3: dischargepatient(); break;
   	case 4: appointment(); break;
   	case 5: about_hospital(); break;
   	case 6: printf("Exiting......"); break;
   	default: printf("Invalid choice");
   }
   }while(choice != 6);
   	return 0;
   }
// *Function Defination*
// *Manager*
void manager(){
    int pass, ch, option, id, i;

    printf("Enter The Manager Password: ");
    scanf("%d", &pass);

    if(pass != 12345){
        printf("Wrong Password!\n");
        return;
    }

    do{
        printf("\n===== MANAGER MENU =====\n");
        printf("1. Add Doctor\n");
        printf("2. Fire Doctor\n");
        printf("3. Add Nurse\n");
        printf("4. Fire Nurse\n");
        printf("5. Add Other Staff\n");
        printf("6. Fire Other Staff\n");
        printf("7. Back\n");
        printf("Enter choice: ");
        scanf("%d", &ch);

        // *ADD DOCTOR* 
        if(ch == 1){
            if(dCount >= 10){
                printf("Doctor limit reached!\n");
            } else {
                printf("Enter Doctor Name: ");
                scanf("%s", doctor[dCount]);
                dCount++;
                printf("Doctor Added | ID = %d\n", dCount);
            }
        }

        // *FIRE DOCTOR*
        else if(ch == 2){
            if(dCount == 0){
                printf("No doctors to fire.\n");
                continue;
            }

            printf("1. Fire One Doctor\n");
            printf("2. Fire All Doctors\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nDoctor List:\n");
                for(i = 0; i < dCount; i++)
                    printf("ID %d | %s\n", i+1, doctor[i]);

                printf("Enter Doctor ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > dCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < dCount-1; i++)
                        strcpy(doctor[i], doctor[i+1]);
                    dCount--;
                    printf("Doctor Fired Successfully!\n");
                }
            }
            else if(option == 2){
                dCount = 0;
                printf("All Doctors Fired!\n");
            }
        }

        // *ADD NURSE*
        else if(ch == 3){
            if(nCount >= 10){
                printf("Nurse limit reached!\n");
            } else {
                printf("Enter Nurse Name: ");
                scanf("%s", nurse[nCount]);
                nCount++;
                printf("Nurse Added | ID = %d\n", nCount);
            }
        }

        // *FIRE NURSE*
        else if(ch == 4){
            if(nCount == 0){
                printf("No nurses to fire.\n");
                continue;
            }

            printf("1. Fire One Nurse\n");
            printf("2. Fire All Nurses\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nNurse List:\n");
                for(i = 0; i < nCount; i++)
                    printf("ID %d | %s\n", i+1, nurse[i]);

                printf("Enter Nurse ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > nCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < nCount-1; i++)
                        strcpy(nurse[i], nurse[i+1]);
                    nCount--;
                    printf("Nurse Fired Successfully!\n");
                }
            }
            else if(option == 2){
                nCount = 0;
                printf("All Nurses Fired!\n");
            }
        }

        // *ADD STAFF*
        else if(ch == 5){
            if(sCount >= 10){
                printf("Staff limit reached!\n");
            } else {
                printf("Enter Staff Name: ");
                scanf("%s", staff[sCount]);
                sCount++;
                printf("Staff Added | ID = %d\n", sCount);
            }
        }

        // *FIRE STAFF*
        else if(ch == 6){
            if(sCount == 0){
                printf("No staff to fire.\n");
                continue;
            }

            printf("1. Fire One Staff\n");
            printf("2. Fire All Staff\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nStaff List:\n");
                for(i = 0; i < sCount; i++)
                    printf("ID %d | %s\n", i+1, staff[i]);

                printf("Enter Staff ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > sCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < sCount-1; i++)
                        strcpy(staff[i], staff[i+1]);
                    sCount--;
                    printf("Staff Fired Successfully!\n");
                }
            }
            else if(option == 2){
                sCount = 0;
                printf("All Staff Fired!\n");
            }
        }

    } while(ch != 7);
}

   
//  *Addpatient*
void addpatient(){
	printf("\nEnter Your Patient Name : ");
	scanf("%s",&patient[pCount]);
	pCount++;
	printf("\n Patient is add | ID = %d\n",pCount);
	
}

//  *Dischargepatient*
void dischargepatient(){
	int i ,id;
	if(pCount==0){
		printf("No patient to discharge.\n");
		return;
	}
    printf("Patient List\n");
    for(i=0;i<pCount;i++){
    	printf("ID %d | %s\n",i+1,patient[i]);
	}
	printf("Enter Pateint ID to dischargepatient \n");
	scanf("%d",&id);
	if(id<1 || id>pCount){
		printf("invalid patient ID.\n");
		return;
	}
	 
	 for(i = id - 1; i < pCount - 1; i++) {
        strcpy(patient[i], patient[i + 1]);
    }

    pCount--;
    printf("Patient Discharged Successfully!\n");
}

//  *Appointment*
void appointment(){
	int i,did;
	if(dCount==0){
		printf("No doctor are avalible\n");
	} 
	else {
	printf("Avalible doctors are\n");
		for(i=0;i<dCount;i++){
			printf("ID %d | %s\n",i+1,doctor[i]);
		}
	}
	printf("Enter doctor ID for appointment \n");
	scanf("%d",&did);
	if(did<1 || did >dCount){
		printf("Invalid doctor ID \n");
		return;
	}
}

//  *About_hospital*
void about_hospital(){
	int i;
	printf("===== Hospital Staff =====\n");
	printf("Avalible doctors\n");
	for(i=0;i<dCount;i++){
		printf("ID %d | %s\n",i+1,doctor[i]);
	}
	printf("Avalible nurses\n");
	for(i=0;i<nCount;i++){
		printf("ID %d | %s\n",i+1,nurse[i]);
	}
	printf("Other staff\n");
	for(i=0;i<sCount;i++){
		printf("ID %d | %s\n",i+1,staff[i]);
	}
}
#include<stdio.h>
#include<conio.h>
#include<string.h>

// *Arrays for naming of variable
   char doctor[10][20];
   char nurse[10][20];
   char staff[10][20];
   char patient[10][20];
   
// *Counters*
   int dCount = 0, sCount = 0, nCount = 0, pCount = 0;
   
// *Funtion Decelaration* 
   void manager();
   void addpatient();
   void dischargepatient();
   void appointment();
   void about_hospital();
   
   int main(){
   	int choice;
    do{
		
   	printf("======= Hospital App =======\n");
   	printf("1. Manager Login\n");
   	printf("2. Add Patient\n");
   	printf("3. Discharge Patient\n");
   	printf("4. Appointment to Doctor\n");
   	printf("5. About Hospital\n");
   	printf("6. Exit\n");
   	printf("--------------------------\n");
   	
   	printf("Enter Your Choice\n");
   	scanf("%d",&choice);
   	
   	switch(choice){
   	case 1: manager(); break;
   	case 2: addpatient(); break;
   	case 3: dischargepatient(); break;
   	case 4: appointment(); break;
   	case 5: about_hospital(); break;
   	case 6: printf("Exiting......"); break;
   	default: printf("Invalid choice");
   }
   }while(choice != 6);
   	return 0;
   }
// *Function Defination*
// *Manager*
void manager(){
    int pass, ch, option, id, i;

    printf("Enter The Manager Password: ");
    scanf("%d", &pass);

    if(pass != 12345){
        printf("Wrong Password!\n");
        return;
    }

    do{
        printf("\n===== MANAGER MENU =====\n");
        printf("1. Add Doctor\n");
        printf("2. Fire Doctor\n");
        printf("3. Add Nurse\n");
        printf("4. Fire Nurse\n");
        printf("5. Add Other Staff\n");
        printf("6. Fire Other Staff\n");
        printf("7. Back\n");
        printf("Enter choice: ");
        scanf("%d", &ch);

        // *ADD DOCTOR* 
        if(ch == 1){
            if(dCount >= 10){
                printf("Doctor limit reached!\n");
            } else {
                printf("Enter Doctor Name: ");
                scanf("%s", doctor[dCount]);
                dCount++;
                printf("Doctor Added | ID = %d\n", dCount);
            }
        }

        // *FIRE DOCTOR*
        else if(ch == 2){
            if(dCount == 0){
                printf("No doctors to fire.\n");
                continue;
            }

            printf("1. Fire One Doctor\n");
            printf("2. Fire All Doctors\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nDoctor List:\n");
                for(i = 0; i < dCount; i++)
                    printf("ID %d | %s\n", i+1, doctor[i]);

                printf("Enter Doctor ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > dCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < dCount-1; i++)
                        strcpy(doctor[i], doctor[i+1]);
                    dCount--;
                    printf("Doctor Fired Successfully!\n");
                }
            }
            else if(option == 2){
                dCount = 0;
                printf("All Doctors Fired!\n");
            }
        }

        // *ADD NURSE*
        else if(ch == 3){
            if(nCount >= 10){
                printf("Nurse limit reached!\n");
            } else {
                printf("Enter Nurse Name: ");
                scanf("%s", nurse[nCount]);
                nCount++;
                printf("Nurse Added | ID = %d\n", nCount);
            }
        }

        // *FIRE NURSE*
        else if(ch == 4){
            if(nCount == 0){
                printf("No nurses to fire.\n");
                continue;
            }

            printf("1. Fire One Nurse\n");
            printf("2. Fire All Nurses\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nNurse List:\n");
                for(i = 0; i < nCount; i++)
                    printf("ID %d | %s\n", i+1, nurse[i]);

                printf("Enter Nurse ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > nCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < nCount-1; i++)
                        strcpy(nurse[i], nurse[i+1]);
                    nCount--;
                    printf("Nurse Fired Successfully!\n");
                }
            }
            else if(option == 2){
                nCount = 0;
                printf("All Nurses Fired!\n");
            }
        }

        // *ADD STAFF*
        else if(ch == 5){
            if(sCount >= 10){
                printf("Staff limit reached!\n");
            } else {
                printf("Enter Staff Name: ");
                scanf("%s", staff[sCount]);
                sCount++;
                printf("Staff Added | ID = %d\n", sCount);
            }
        }

        // *FIRE STAFF*
        else if(ch == 6){
            if(sCount == 0){
                printf("No staff to fire.\n");
                continue;
            }

            printf("1. Fire One Staff\n");
            printf("2. Fire All Staff\n");
            printf("Enter option: ");
            scanf("%d", &option);

            if(option == 1){
                printf("\nStaff List:\n");
                for(i = 0; i < sCount; i++)
                    printf("ID %d | %s\n", i+1, staff[i]);

                printf("Enter Staff ID to fire: ");
                scanf("%d", &id);

                if(id < 1 || id > sCount){
                    printf("Invalid ID!\n");
                } else {
                    for(i = id-1; i < sCount-1; i++)
                        strcpy(staff[i], staff[i+1]);
                    sCount--;
                    printf("Staff Fired Successfully!\n");
                }
            }
            else if(option == 2){
                sCount = 0;
                printf("All Staff Fired!\n");
            }
        }

    } while(ch != 7);
}

   
//  *Addpatient*
void addpatient(){
	printf("\nEnter Your Patient Name : ");
	scanf("%s",&patient[pCount]);
	pCount++;
	printf("\n Patient is add | ID = %d\n",pCount);
	
}

//  *Dischargepatient*
void dischargepatient(){
	int i ,id;
	if(pCount==0){
		printf("No patient to discharge.\n");
		return;
	}
    printf("Patient List\n");
    for(i=0;i<pCount;i++){
    	printf("ID %d | %s\n",i+1,patient[i]);
	}
	printf("Enter Pateint ID to dischargepatient \n");
	scanf("%d",&id);
	if(id<1 || id>pCount){
		printf("invalid patient ID.\n");
		return;
	}
	 
	 for(i = id - 1; i < pCount - 1; i++) {
        strcpy(patient[i], patient[i + 1]);
    }

    pCount--;
    printf("Patient Discharged Successfully!\n");
}

//  *Appointment*
void appointment(){
	int i,did;
	if(dCount==0){
		printf("No doctor are avalible\n");
	} 
	else {
	printf("Avalible doctors are\n");
		for(i=0;i<dCount;i++){
			printf("ID %d | %s\n",i+1,doctor[i]);
		}
	}
	printf("Enter doctor ID for appointment \n");
	scanf("%d",&did);
	if(did<1 || did >dCount){
		printf("Invalid doctor ID \n");
		return;
	}
}

//  *About_hospital*
void about_hospital(){
	int i;
	printf("===== Hospital Staff =====\n");
	printf("Avalible doctors\n");
	for(i=0;i<dCount;i++){
		printf("ID %d | %s\n",i+1,doctor[i]);
	}
	printf("Avalible nurses\n");
	for(i=0;i<nCount;i++){
		printf("ID %d | %s\n",i+1,nurse[i]);
	}
	printf("Other staff\n");
	for(i=0;i<sCount;i++){
		printf("ID %d | %s\n",i+1,staff[i]);
	}
}
