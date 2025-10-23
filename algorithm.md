Write "Do you prefer hot or cold cereals for breakfast?" 
Read typePref 
Set list1 to empty 
FOR each cereal IN cereals 
    IF cereal.type == typePref 
    ADD cereal TO list1 
END FOR 
Set remaining = count(list1) 
Write "After chosing {typePref} cereals, {remaining} options remain."

Write "How important is your calory intake for you? Please answer by writing: important, matters or not important" 
Read calPref 
IF calPref = "important" 
    set maxCalories 50 
ELSE IF calPref ="matters" 
    set maxCalories 80 
ELSE set maxCalories 999 
set list2 to empty 
FOR each cereal in list1 
 IF cereal.calories <= maxCalories 
 ADD cereal TO list2 
END FOR 
Set remaining = count(list2) 
Write "After this choice you have {remaining} cereals left."

Write "Would you say that you have a sweet tooth? i.e should your cereals be sweet? Yes/No" 
Read sweetTooth 
Set list3 empty 
IF sweetTooth = "yes" 
    FOR each cereal in list2 
        IF cereal.sugar >10 
        ADD cereal TO list3 
    END FOR 
ELSE 
    FOR each cereal in list2 
        IF cereal.sugar <=10 
        ADD cereal TO list3 
    END FOR 
Set remaining = count(list3) 
Write "You have now reached the final step and have {remaining} cereals left."

Write "Is fiber important to you?"
Read fiberPref
Set finalList = list3
IF fiberPref = "yes"
    SORT finalList BY fiber DESCENDING
END IF
Write "Here are your best matches!"
FOR each cereal IN finalList
    Write cereal.name, cereal.type, cereal.calories, cereal.sugar, cereal.fiber
END FOR
