# genetic_algorithm
 There are many applications where Genetic Algorithm can be used especially where one does not know the exact solution and how to find it. One such problem is '8 Queens' puzzle. The objective here is to place 8 queens on a Chess board of dimension 8x8 such that they don’t threaten each other i.e. no 2 queens share the same row, column and diagonal. There are only 92 solutions which meet the criteria out of 16,777,216 possible combinations.

 I tried my hand of solving this problem applying Genetic Algorithm. Some of steps and results are outlined below. The coding was done in Pytho and here is URL to notebook on Github

 1. Initial Population : First objective is to generating random 15 solutions which can be used as seed : say as an example below is example solution where the column position indicates the column in which the Queen is present and the number indicates the row


If one was to visualize this particular solution on chess board , it would look like below

2. Fitness Score: As you can see above there are few queens in positions where they can attack each other ; so we would develop a function that returns the fitness score of the solution. The fitness score adds up any possibilities that are there for the queens to attack. So ideally we are looking to achieve fitness score of 0 and any higher number is not good. Once all initial 15 models are scored , we would rank them in the ascending order of the fitness scores.

            Solution       FitnessScore

0  [6, 3, 7, 0, 5, 3, 1, 4]            4

1  [3, 6, 0, 2, 7, 7, 1, 1]            6

2  [1, 5, 7, 2, 6, 1, 3, 5]            6

3  [6, 3, 6, 5, 2, 4, 6, 7]            7

4  [2, 1, 3, 3, 7, 0, 3, 3]            7

5  [1, 0, 1, 0, 7, 4, 2, 6]            7

6  [1, 7, 1, 1, 6, 4, 4, 0]            8

7  [0, 7, 3, 6, 0, 6, 2, 6]            8

8  [0, 3, 5, 1, 4, 3, 2, 2]            8

9  [0, 7, 2, 3, 0, 1, 2, 5]            9

10 [5, 1, 1, 3, 3, 4, 5, 3]            9

11 [6, 5, 0, 5, 3, 3, 0, 5]           10

12 [0, 2, 2, 3, 5, 1, 0, 1]           10

13 [4, 2, 7, 3, 4, 4, 7, 3]           10

14 [2, 3, 6, 3, 0, 5, 2, 5]           11

3. Crossover and Mutation : What we do next is pick the 2 solutions with least fitness scores and apply Crossover and Mutation techniques. Lets start with the solutions and name them as Parent 1 and 2

Parent 1 [6, 3, 7, 0, 5, 3, 1, 4] with score 4

Parent 2 [3, 6, 0, 2, 7, 7, 1, 1] with score 6

As we look at creating a cross over solution, given that there are 8 values , we would take cross over point as 4

Cross over child 1 [6, 3, 7, 0, 7, 7, 1, 1] by combining first half of Parent 1 and second half of Parent 2

Cross over child 1 [3, 6, 0, 2, 5, 3, 1, 4]by combining second half of Parent 1 and first half of Parent 2

Then we apply Mutation by randomly changing one of the columns with a random value between 0-7

Crossover child 1 after Mutation [6, 3, 7, 0, 4, 7, 1, 1] with score of 5 -Not better than one of parents

Crossover child 2 after Mutation [3, 7, 0, 2, 5, 3, 1, 4] with score of 4 -Better than one of parents

Now we add these next gen solutions back to our original set of solutions and sort that dataset again on Fitness Score ascending. Then, we begin from Step 3 again and reiterate in loops (1000 to begin with). We sort solutions on Fitness score (ascending) before each iteration to ensure that we would use best solutions to create next generation solution.

Keep in mind that since we are doing the picking of original solution randomly as well as mutation with random number, while its guaranteed that your solution fitness score improves with iterations, there is a possibility that your run may not always return a winning combination. So what does success look like - In an execution that started with above initial population, only after 27 iterations, I got a solution which solved the problem i.e. fitness score of 0 or no queens in attack positions . Now, how beautiful is that?
