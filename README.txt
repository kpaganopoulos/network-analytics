HW1 (individual) Network Analytics (MSc BA, 2020) Due on 28-02-2020 23:00
Individual: Has to be done on your own without any consultation of people or sources except as specified below. The HW has 60 points total and no individual feedback will be given, but solutions with class-level feedback will be posted after grading.
Start early as they may take some time to do.
Theory: You develop a feeling for graphs and their manipulation and objects only by doing some theory. For the following give a proof --- i.e., rigorous inductive reasoning, and in your own words. Draw to develop intuition, but a picture is not a proof.
1. (10 points) A directed graph is strongly connected if there is a (directed) path from every node to every other node. Show that in a directed strongly connected graph containing more than one node, no node can have a zero indegree or a zero outdegree.
2. (10 points) Show that every tree is a bipartite graph.
3. (10 points) A directed acyclic graph (DAG) is a directed graph without cycles (the underlying graph may have cycles, so it is not a tree). Show that a DAG has a labeling of its nodes (that is a labeling 1, …, n of its nodes) such that every arc goes from a lower-numbered node to a higher-numbered node. (You need to find a way to do it, and also show that is always possible.)
These DAGs are ubiquitous in neural networks (used for visual recognition), Hidden-Markov models (used for speech recognition) and in general, graphical models.
NOTE: These is basic graph theory and you will find the answers in any graph theory book (although it would be faster to think through than search). Please take care of writing the answer in your own words in any case!
NetworkX Exercise
Programming: besides the documentation, you are allowed to search forums (but not consult or ask your cohort). The final code has to be written and debugged entirely on your own: Part of the learning objective is to search and choose for the best nx, pandas or numpy function.
PLEASE SUBMIT ALL CODE AS Jupyter html files ONLY
This is based on the data file called HW1_asset_prices.csv. This represents the price movements of a set of assets (bonds, stocks etc., their description is quite irrelevant here).
Economists and investors are very interested in the correlation of asset prices, both to understand risk, as well as (hopefully) find correlation to lagged asset prices for investing. A correlation matrix with N assets is an N × N matrix of correlations. See https://en.wikipedia.org/wiki/Stock_correlation_network for some background information.
Your task is to visualize the correlation matrix in network form. You are free to use any python package for your calculations in a (numpy, scipy, pandas etc.) as you see fit. For b and c, I expect you to use the matplotlib.pyplot interface in NetworkX. You can gain the +5 point if you (i) submit in Jupyter notebook format (ii) interface to any external drawing packages such as graphviz to call one of their drawing functions.
Get a skeleton code working to do the tasks (can be done in under 10 lines of code with the right built-in functions in pandas and networkx) and then enhance and explore from there on.
a. (10 points) Calculate the correlation matrix (you may have to use your Stats and Econometrics knowledge here)
b. (10 points) With assets as nodes, plot the matrix as a network. Experiment with the different graph layouts and choose the one that you believe is best, and explain why
c. (10 points) Enhance your plot by representing the thickness of the edges and size of the nodes to give some insight.

HW2
Network Analytics, MSc BA, 2019_20
Due by 13 March 2020, 11PM
Programming: You are allowed to consult on the programming part with your colleagues and on the web but the final code has to be written and debugged entirely by your group.
In the following, you have to search for the appropriate functions in NetworkX/numpy/scipy yourselves.
1. (10 points) In a previous cohort I asked the students to write down the number of emails they exchanged with other members of the cohort. Data might be having some problems, but we proceed nevertheless. Use built-in functions in NetworkX on the data HW2_ who_talks_to_whom.xlsx to do an organizational network analysis report (1 page max)---essentially calculating centrality measures (try at least one eigenvalue based one) and clustering coefficients and gaining some insight into the network. The objective for me (your client) is to identify who are the leaders and opinion-makers in the cohort, and any other qualitative insights you might obtain.
2. [15 points]
For this problem, you don’t need to program from scratch but just modify the TSP example program on the gurobi website.
The data HW2_qatar_tsp.txt contains latitude and longitude data of 194 cities from Qatar. Calculate the distance matrix (use an approximation like here which is quite accurate for short distances; or use packages like haversine or geopy). The x and y-cordinates are the latitude and longitude in decimal form multiplied by 1000. EUC_2D means take these as Cartesian co-ordinates. Can also use haversine treating them as longitude and latitude. You are free to use any other functions you find.
a. (5 points) Plot the latitude and longitude as a scatter plot using a drawing package (some options are: matplotlib basemap toolkit (the most advanced, but also the most difficult to use), geopy, gmplot, plotly …). It should look roughly like this.
b. [5 points] The most powerful integer programming solver is Gurobi (along with CPLEX). They give a free one-year license if you download and install from a University IP address. Use the most powerful computer you have in your group (cores and memory).
Connect with the Python interface of Gurobi and find an optimal tour using the sub-tour elimination integer programming formulation we did in class. You cannot generate all the sub-tour elimination constraints at once (too many).
Instead, (the example program on Gurobi) does the following standard algorithm technique to solve problems with an exponential number of constraints:
i. Start with a problem with only the degree =2 constraints.
ii. Check the resulting solution for sub-tours. If there is a sub-tour, add the sub-tour elimination constraints corresponding to a cut defined by the sub-tour (i.e. you are eliminating that sub-tour in the next round).
iii. Repeat till you find a tour (in which case, it is optimal). Make sure you do not discard the solution from the previous round, but start from what you had found.
This method of generating constraints on the fly is suitable when the number of constraints are exponential in the problem size. The dual version of this is called column generation. Compare the optimal solution with the or-tools solution.
c. (5 points) Plot the resulting tour on the scatter plot. The optimal tour should look like this:
3. (15 points)
a. Formulate the problem of sending the maximum amount of flow from Node 1 to
Node 5 in the following network (the edges have capacities as shown in the figure) as a linear program
b. Formulate and solve the dual using a linear programming solver (say Excel; Hint: do
you really need to solve the dual, or solving the primal is enough?)
Define a s-t Cut as a partition of V into disjoint sets S, T (i.e., S T= V and S T = ) with
s in S and t in T.
Define capacity of the cut, Cap(S, T) = sum of the capacities of edges from S to T
Define Flow across the cut, Flow(S,T): net flow out of S = sum of flows out of S - sum of
flows into S.
c. A very famous and central theorem in combinatorial optimization states: Max-flow =
Value of Min-cut (Max-flow/Min-cut theorem). Proving Max-flow ≤ Value of Mincut
is easy---give a reason why this should be so.
d. (challenging) From the dual values (i.e. the shadow prices) of the linear program
corresponding to the optimal extreme point (basic feasible) solution, find a minimumcapacity
cut. (The cut itself would be easy to find by inspection, but you have to come
up with a connection between the dual values and the cut; examining the solution
values would give you a clue).

HW3
Network Analytics, MSc BA, 2019_20
Submission by 25 March
Programming: You are allowed to consult on the programming part with your colleagues and on the web but the final code has to be written and debugged entirely on your own. You have to search for the appropriate functions in NetworkX/numpy/scipy yourselves.
1. The exercise is on detecting communities in two networks
i. The small Zachary Karate Club network with known community ground-truth
ii. The who-talks-to-whom network of HW 2 (underlying undirected graph where you put an edge if there is a directed link in either direction between two nodes)
For both these networks, you may have to use the networkx functions to go back and forth between edge_list format and adjacency matrix format depending on which community detection package and method you are using. Trying out various graph layouts might help gain some insight.
(a) (10 points) Calculate the community structure using the networkx girvan_newman algorithm
(b) (10 points) the Louvain community package that finds best modularity partition via some fast heuristics. Note that the class data is in a 0-1 matrix format. You may want to transform it to adjlist format → write to file and →reread, or read each line and add one edge at a time
(c) (10 points) Plot the communities you obtained with different communities in different colors, and for best effect to give insight. (Hints: http://perso.crans.org/aynaud/communities/api.html; http://ryancompton.net/2014/06/16/community-detection-and-colored-plotting-in-networkx/)
2. (10 points) From the Bass Model article in Week 5 folder (first, relate it to the model and terminology we did in class) and the data for the DOCTOR movie (Table 8.7), obtain a rolling-horizon estimate of the parameters (using the optimization model described) for a forecast after observing the sales till week 4. Compare them with the estimates and actual observed demand in the article. You are free to use any regression package and language (R, Excel Data Toolpak, Python).
3. (10 points) The following represents the evolution of a slice of European banking over time. You need not use any formal model, but by plotting wisely extract some insight into the
propagation of economic shocks. Your are of course free to use general knowledge of financial history in the recent past.
The dataset xasset_prices.csv contains data of the banking system from [from_id] country has an exposure of value [value] to entities in [to_id] country at date [net_id]. Extract some insight into the propagation of economic shocks.
