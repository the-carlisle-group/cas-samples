The Export object creates a copy of your data in the file format of your choice.

# Notes
- A file will be created for every unique value in your grouping field.  You can think of this as an id.
- Grouping is case-sensitive but the Windows file system is not.  TEST, test, and TeSt create separate groups.  The application will warn teh user and add a unique ID value to each file. You can recalculate your field standardizing the data if this is an issue.

   ![image](https://user-images.githubusercontent.com/5807754/113605678-9811a800-960c-11eb-8857-d0f11f2905b9.png)
   ![image](https://user-images.githubusercontent.com/5807754/113606256-61885d00-960d-11eb-8589-dc02408cb3e9.png)

- All records, unless not flagged by Selection Criteria, will be exported in the order they appear in the CAS file.
- Export file name will include the group value by default.  Feature available CAS 6.0.1030+
- Filename can be customized using two new string replacement options, <id> and <value>.  <id> give a unique numeric count of the group, which is how CAS has worked until version 6.0.1030.  <value> will input the group value into the filename.  This is new default behavior. 
  - &lt;id&gt;
  
    ![image](https://user-images.githubusercontent.com/5807754/113606553-cba10200-960d-11eb-8202-b7c6e6fa2f4b.png)
    ![image](https://user-images.githubusercontent.com/5807754/113607130-79acac00-960e-11eb-8340-7a125c62bd39.png)

  - &lt;value&gt;
  
    ![image](https://user-images.githubusercontent.com/5807754/113607176-86c99b00-960e-11eb-9023-a6e89cc9eb5f.png)
    ![image](https://user-images.githubusercontent.com/5807754/113607315-af519500-960e-11eb-802b-3d59627c92a0.png)

  - Custom Combination

    ![image](https://user-images.githubusercontent.com/5807754/113607504-e3c55100-960e-11eb-9230-9994448cf7bb.png)
    ![image](https://user-images.githubusercontent.com/5807754/113607484-dd36d980-960e-11eb-8128-19222fd0e35e.png)
    
- Filename <value> text will be the literal or Field Code if defined in the File->Codes menu.  This can be changed in the System->File Options menu.

    ![image](https://user-images.githubusercontent.com/5807754/113608807-a1047880-9610-11eb-91c7-ae93749825d6.png)

  - Codes

    ![image](https://user-images.githubusercontent.com/5807754/113609193-13755880-9611-11eb-9b91-8b4fe5d13fc9.png)
    
  - No Codes

    ![image](https://user-images.githubusercontent.com/5807754/113609256-24be6500-9611-11eb-9218-9266bbe2d5f7.png)
    ![image](https://user-images.githubusercontent.com/5807754/113609320-36a00800-9611-11eb-8b59-4db92acf2e15.png)


# How-To

#### Enable Grouping

Select your grouping field or partition in teh main Selection Criteria->Group tab.  

![image](https://user-images.githubusercontent.com/5807754/113605202-f1c5a280-960b-11eb-912a-12117197d8ca.png)

#### Create New Export Object

Right click, select New, Object and Export.

![image](https://user-images.githubusercontent.com/5807754/113604283-a8c11e80-960a-11eb-9167-de700c9c1830.png)

#### Define Export Object Properties

Minium the Export File Name and File Type is required.  Resulting filename will be baed on the group value and any replacement parameters.  See notes above.

![image](https://user-images.githubusercontent.com/5807754/113607693-225b0b80-960f-11eb-985a-d80d75ff5b76.png)

