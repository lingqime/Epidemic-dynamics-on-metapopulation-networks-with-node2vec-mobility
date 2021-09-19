# Epidemic-dynamics-on-metapopulation-networks-with-node2vec-mobility

The data sets, numerical simulations, and Python codes are all presented in this directory.

All the data sets are included in the folder `data set`. The ER random graph, BA model, Random clustered graph, Power-law cluster graph, Geographical threshold graph, LFR model, US airport network, Manizales network presented in the paper are named as `ER-100-6-1.txt`, `BA-100-3-1.txt`, `random clustered graph indpendent 1.txt`, `powerlaw cluster graph p=0.5.txt`, `geographical threshold graph with threshold 80.txt`, `LFR model small mu.txt`, `USAir97-unweighted.txt`, and `colombian.txt`, respectively.

The code of Euler method in Fig. 2 and its Monte Carlo simulation is presented in `Fig. 2 Euler method and Monte Carlo simulation.ipynb`. For Euler method (cell [8]), the stepsize `h = 0.01` and its iteration times `iteration = 30000`. For Monte Carlo method (cell [11]), the stepsize `dt = 0.01` and it iterated 30000 times. (See the figure below). 


![Euler method](https://github.com/lingqime/Epidemic-dynamics-on-metapopulation-networks-with-node2vec-mobility/blob/main/images/image_1.png)

Here are some explanations for the loop below:

`for beta in np.linspace(0.002, 0.03, 15):` represents the infection rate, `beta = 0.002, 0.004, ..., 0.03`, respetively. We assume `rho = 50`. Therefore, `rho*beta = 0.1, 0.2, ..., 1.5`, respectively.

Given the infection rate `beta` and each configuration `(a, b)`, we will run the Monte Carlo simulation 100 times. It is represented by the loop `for ITERATION in range(0, 100):`.

`for iteration in range(0, 30000):` represents the times of iteration for each simulation. Because we assume `dt = 0.01` above, the total time in the model is `t = 0.01*30000 = 300` unit time.

`arr = [[random.choice(Directed_edges), 'S'] for i in range(0, rho*(N - 1))]` and `arr = arr + [[random.choice(Directed_edges), 'I'] for i in range(0, rho)]` represents that there are 1% individuals initially infected. One can customize by chaning the initial condition here.

`for i in range(0, len(arr)):` represents that we are considering the reaction process for each individual.

![Monte Carlo iteration](https://github.com/lingqime/Epidemic-dynamics-on-metapopulation-networks-with-node2vec-mobility/blob/main/images/image_2.png)

In `Fig. 2 Euler method and Monte Carlo simulation.ipynb`, we only showed that the diffusion process for `(a,b) = (0.1,0.1)`. If one can change the code
`next_edge = random.choices(Directed_edges, weights = T1[Directed_edges.index(arr[i][0])])[0]` to consider other combinations of `(a,b)`. For example, 

`T2[Directed_edges.index(arr[i][0])])[0]` represents `(a,b) = (5, 0.1)`

`T3[Directed_edges.index(arr[i][0])])[0]` represents `(a,b) = (0.1, 5)`

`T4[Directed_edges.index(arr[i][0])])[0]` represents `(a,b) = (5, 5)`

![Diffusion process](https://github.com/lingqime/Epidemic-dynamics-on-metapopulation-networks-with-node2vec-mobility/blob/main/images/image_3.png)

### A short remark: 
Monte Carlo simulation is sensitive to the initial condition. For example, if we assume that there are 1% individuals or all individuals initially infected, choice of the stepsize `t = 0.01` is safe. However, if the initial condition is that there is only one individual initially infected, then the safe initial condition is `t = 10^{-4}`. Otherwise, one will see that the individual is very likely to recover before he/she propagate disease to the other individuals.

### Another remark:
We saved the simulation results with different inital conditions in the folders `Monte Carlo simulation one percent`, `Monte Carlo simulation all infected`, and `Monte Carlo simulation one infected`, repectively. It is very time consuming for us to run the Monte Carlo simulations. Therefore, we truncated the loop into small pieces and saved the results by parts. `data1`, `data2`, `data3`, and `data4` represents `(a,b)=(0.1, 0.1)`, `(a,b)=(5, 0.1)`, `(a,b)=(0.1, 5)`, `(a,b)=(5, 5)`, respectively. `part1`,...,`part15` represents `rho*beta = 0.1,...,1.5`, respectively. For example, the filename `list_new_data2_part5.npy` represents the Monte Carlo simulation results under the condition `(a, b) = (5, 0.1)` and `beta*rho = 0.5`.

After obtaining all the results (Euler method and Monte Carlo simulation) from `Fig. 2 Euler method and Monte Carlo simulation.ipynb`, one can use the file `Plot Fig. 2.ipynb` to visualize the results. However, you need to TeX installed on your local computer before running `Plot Fig. 2.ipynb`. For details, please see https://matplotlib.org/stable/gallery/text_labels_and_annotations/tex_demo.html

The heat map matrices presented in Figs. 4 and 5 are contained in the folder `Numerical results`. One can discern them by their nomenclatures. For example, `Epidemic threshold via ER-100-6-1 a, b.npy` represents the epidemic threshold on ER random graph in terms of a and b, i.e., Fig. 4(a) in the paper. 

All the numerical results were fulfilled by [Jupyter Notebook](https://jupyter.org/). The codes can be found in the folder `Codes`.

If there is any question, please email lingqime@buffalo.edu or lingqime@gmail.com.
