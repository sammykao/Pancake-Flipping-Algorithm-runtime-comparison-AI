# PANCAKE PROBLEM
    - Given a random stack of randomly assorted pancakes of adjacent size 1-10,
    and a actuator of only being able to flip a pancake from position n up, 
    find a solution that will sort the pancakes from size 10->1 (Bottom to top).
    - So, given stack [4, 3, 2, 1, 6, 7, 9, 5, 8, 10], we would want to flip them 
    until we get [10, 9, 8, 7, 6, 5, 4, 3, 2, 1].

### REPRESENTING AS A SEARCH PROBLEM ###
    - To define our problem as a search problem, we need to define the 5 key
    tenants of a search strategy
        1. Initial State: The initial state our agent starts in is the initial
        randomly assorted stack (list) of pancakes
        2. Possible Actions Available: To traverse through our theoretical graph
        of states, we have define possible actions as neighbors to our states.
        These 'neighbors' are possible flips we can take in which we insert 
        our spatula into certain gaps. The gaps/neighbors available are
        all possible gaps that we can insert into
        3. Successor Function: The successor function is us flipping our pancake
        stack, and so in a technical aspect, the list will now have elements
        flipped.
        4. Goal Test: The Goals State is when all the pancakes sorted 10->1
        5. Path Cost Function: The path cost of an action will be how many 
        pancakes we flip. Rather than just simply representing the
        cost as uniformly 1 as every action, we can actually use a more efficient
        cost function. Flipping more pancake will be more disruptive, 
        thus we can penalize this.

### ALGORITHMS & HEURISTICS: ####
    - Our heuristic cost function uses the gap cost of the stack. This 
    cost is the amount of gaps with pances that are not size adjacent.
    This was implemented for the A* algorithm, which calculates distance
    to our goal state. 
    - We create timing data in our program to measure performance for
    the user. Using an input if [4, 3, 2, 1, 6, 7, 9, 5, 8, 10], UCS
    performs at 3.44 seconds, while A* performs in 0.15 seconds. 
    Clearly, the gap heuristic and A* function works as desired

### ASSUMPTIONS: ###
    - For specifications of problem, we asssume that the input
    sizes are 10, with 1 through 10 values. We catch any input errors,
    since we made the user input the stack themselves. If it does not
    the exact format, then an error will be raised
    - We assume their is no inherent cost to flip the pancakes, thus
    are able to determine whatever cost will improve runtime of the 
    program.
    - We assume that the starting index in our python list is the bottom
    with the back being the top
    - We assume that the solution should be 1 indexed, since
    the gap heuristic published work used 1 indexing while referring to 
    the pancake stack


