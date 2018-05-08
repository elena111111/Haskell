є5 ќпределите функцию, котора€ увеличивает элементы исходного списка на единицу.

```Haskell
inc :: [Integer] -> [Integer]
inc [] = []
inc (x:xs) = [x + 1]++(inc xs) 

--test
print (inc [2, 3, 0, -1, 7])
[3,4,1,0,8]
```

є7 ќпределите функцию, удал€ющую из исходного списка элементы с четными номерами.

```Haskell
del_even :: [a] -> [a]
del_even [] = []
del_even (x:[]) = [x]
del_even (x:xs) = [x]++(del_even (tail xs)) 

--test
print (del_even [2, 3, 0, -1])
[2,0]
print (del_even [2, 3, 0, -1, 7])
[2,0,7]
print (del_even [2, 1])
[2]
print (del_even [2])
[2]
```

є12 ќпределите функцию, замен€ющую в исходном списке два подр€д идущих одинаковых элемента одним.

```Haskell
delete_repeat [] = []
delete_repeat (x:[]) = [x]	--т.к. голову от пустоты не можем вз€ть
delete_repeat (x:xs) = (\res_tail -> 
                            if x == (head xs) 
                            then res_tail
                            else x:res_tail) (delete_repeat xs)

--test
print (delete_repeat [2, 2, 1, 5, 5, 5, 7, 7, 7, 7, 2])
[2,1,5,7,2]
```

є13 ќпределите функцию, удал€ющую в исходном списке все повторные вхождени€ элементов.

```Haskell
member1 a [] = False
member1 a (x:xs) = if a == x 
                   then True
                   else (member1 a xs)

delete_all_repeat [] = []
delete_all_repeat (x:xs) = (\res_tail -> 
                            if (member1 x xs) 
                            then res_tail
                            else x:res_tail) (delete_all_repeat xs)

--test
print (delete_all_repeat [2, 2, 1, 5, 5, 5, 7, 7, 7, 7, 2])
[1,5,7,2]
```

є31 ќпределите функцию (ѕ≈–¬џ…-—ќ¬ѕјƒјёў»… х у), котора€ возвращает первый элемент, вход€щий в оба списка х и у, в противном случае NIL.

```Haskell
first_coincident [] y = []
first_coincident (x:xs) y = if (memory1 x y)
                            then [x]
                            else (first_coincident xs y)
                         
--test
print (first_coincident [3, 4, 0, 5, 7] [2, 1, 5, 7, 5])
[5]
print (first_coincident [3, 4, 0, -1] [2, 1, 5, 7, 5])
[]
print (first_coincident [4] [])
[]
```