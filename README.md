# Haskell
zadachi ot chasovete 
 ```-- po 2 vsqko ot chislata 
doubleVal [] =[]
doubleVal list = (head list)  * 2: doubleVal (tail list)
doubleVal' (x:xs) =x*2 : doubleVal xs 
doubleValMap list =map (\xs -> xs *2) list 

main= do 
  input <-getLine
  let nums= read input :: [Integer]
  print(doubleVal nums)


[1, 2, 5, 6, 8]
(x:xs)

x(head list)-1
xs(tail list)-[2, 5, 6, 8]

d(x:xs)= x*2 : d xs

--obqsnenie
d[8]=2* 8 : d[] --[16]
d[6,8]=2* 6 : d[8]--[12,16]
d[5,6,8]=2* 5 : d[6,8]--[10,12,16]
d[2,5,6,8]=2* 2 : d[5,6,8]--[4, 10, 12, 16]
d[1,2,5,6,8]=2* 1 : d[2,5,6,8]--[1,4,10,12,16]

--obrushtane na spisuk 
reverse'[]=[]
reverse' (x:xs)= (reverse' xs) ++ [x]
main=do
  input <- getLine
  let nums= read input :: [Integer]
  print(reverse nums)
  print(reverse' nums)

Input:
[1,2,3,5]
Output:
[5,3,2,1]
[5,3,2,1]



--broi elementi v masiv 
lengthloop [] result=result
lengthloop (x:xs) result= lengthloop xs (result + 1)
length' list =lengthloop list 0

main=do
  input <- getLine
  let nums= read input :: [Integer]
  print(length' nums)

Input:
[1,5,6,7,8,9,2,5]
Output:
8


--- duplirane
duplicate [] =[]
duplicate (x:xs)= [x,x] ++ (duplicate xs)

main = do
  input <- getLine
  let nums= read input :: [Integer]
  print(duplicate nums)

Input:
[1,2,3]
Output:
[1,1,2,2,3,3]

--removes Nth elements 
removeNthel list result index n=
  if index <= (length list) then -- sravnoto garantirame che minavame prez posledniq element
    if (mod index n) /=0 then 
      removeNthel list (result ++ [list !! index ]) (index+1) n 
    else
      removeNthel list result (index + 1) n 
    else
      result
      

main = do
  input <- getLine
  let nums= read input :: [Int]
  input2 <- getLine
  let n = read input2 :: Int
  print(removeNthel nums [] 1 n)

--fibonachi
fibloop list index n=
  if index < n then 
    fibloop (list  ++ [list !! (index -1) + list !! (index-2)]) (index + 1) n
  else
    list
      
fib n =fibloop [1,1] 2 n 

main = do
  input <- getLine
  let nums= read input :: Int
  print(fib nums)
