Download Link: https://assignmentchef.com/product/solved-ee381-lab-1-stochastic_experiments
<br>



As mentioned in class, there are many ways to model stochastic experiments. The following two programs simulate the toss of a fair coin  N times, and calculate the experimental probability of getting heads (p_heads) or tails (p_heads). Both programs provide the same results, but they differ in the way the models are coded.

<ul>

 <li>The first model is programmed in Python using “for loops”.</li>

 <li>The second model makes use of the arrays, and it is computationally very efficient.</li>

</ul>




<table width="492">

 <tbody>

  <tr>

   <td width="492"><strong>MODEL 1  </strong></td>

  </tr>

  <tr>

   <td width="492">import numpy as np def coin(N):heads, tails = 0, 0     for k in range(0,N):         coin=randint(0,2)         if coin==1:heads=heads+1         else:tails=tails+1#p_heads=heads/N     p_tails=tails/Nprint(‘probability of heads = ‘, p_heads)     print(‘probability of tails = ‘, p_tails) </td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong> </strong>

<table width="426">

 <tbody>

  <tr>

   <td width="426"><strong>MODEL 2 – MORE EFFICIENT CODE </strong></td>

  </tr>

  <tr>

   <td width="426">import numpy as np def coin2(N):coin=randint(0,2,N)     heads=sum(coin)     tails=N-heads#p_heads=heads/N     p_tails=tails/Nprint(‘probability of heads = ‘, p_heads)  print(‘probability of tails = ‘, p_tails) </td>

  </tr>

 </tbody>

</table>

0.2.   Roll of Two Fair Dice; Probability Mass Function (PMF)

This experiment models the roll of a pair of dice for N times. The sum each roll is recorded, and stored in vector “s”. The probability of each possible outcome is calculated and plotted in a  “Probability Mass Function”  (PMF) plot

To create the plots, the simulation has been run for N=100000 times.




<table width="655">

 <tbody>

  <tr>

   <td width="655"><strong>SUM  OF  THE ROLLS  OF  TWO FAIR DICE </strong></td>

  </tr>

  <tr>

   <td width="655">   import numpy as np    import matplotlibimport matplotlib.pyplot as plt# def sum2dice(N):d1=randint(1,7,N)     d2=randint(1,7,N)     s=d1+d2b=range(1,15) ; sb=size(b)     h1, bin_edges = histogram(s,bins=b)     b1=bin_edges[0:sb-1]     close(‘all’)#fig1=plt.figure(1)     plt.stem(b1,h1)plt.title(‘Stem plot – Sum of two dice’)     plt.xlabel(‘Sum of two dice’)     plt.ylabel(‘Number of occurrences’)     fig1.savefig(‘1 EE381 Proj Stoch Exper-1.jpg’)#fig2=plt.figure(2)     p1=h1/N     plt.stem(b1,p1)plt.title(‘Stem plot – Sum of two dice: Probability mass function’)     plt.xlabel(‘Sum of two dice’)plt.ylabel(‘Probability’)fig2.savefig(‘1 EE381 Proj Stoch Exper-2.jpg’) </td>

  </tr>

 </tbody>

</table>

<h2>0.3.   Generating an unfair three-sided die</h2>

This example models the roll of a 3-sided die, with non-uniform probabilities. The die has three sides [1,2,3] with probabilities: [<em>p p p</em><sub>1</sub>, <sub>2</sub>, <sub>3</sub>] = [0.3, 0.6, 0.1].

The experiment simulates the roll of the die for N=10,000 times, and the outcome of the N rolls is plotted as a stem plot. The stem plot verifies that the three sides of the die follow the required probabilities.




The following code will simulate <strong>a single roll</strong> of the three-sided die. The variable “d” represents the number after the roll.




<table width="397">

 <tbody>

  <tr>

   <td width="397">import numpy as np# n=3p=array([0.3, 0.6, 0.1]) cs=cumsum(p)  cp=append(0,cs) r=rand() for k in range(0,n):     if r&gt;cp[k] and r&lt;=cp[k+1]:d=k+1 </td>

  </tr>

 </tbody>

</table>




The following code will simulate the rolling of the three-sided die for N=10,000 times and will plot the outcome as a stem plot.




<table width="590">

 <tbody>

  <tr>

   <td width="590">import numpy as np import matplotlibimport matplotlib.pyplot as plt # def ThreeSidedDie(p):N=10000     s=zeros((N,1))     n=3# p=array([0.3, 0.6, 0.1])     cs=cumsum(p)      cp=append(0,cs)     #     for j in range(0,N):r=rand()         for k in range(0,n):             if r&gt;cp[k] and r&lt;=cp[k+1]:d=k+1         s[j]=d# </td>

  </tr>

  <tr>

   <td width="590"> # Plotting             b=range(1,n+2)     sb=size(b)h1, bin_edges=histogram(s, bins=b)     b1=bin_edges[0:sb-1]     close(‘all’)     prob=h1/Nplt.stem(b1,prob)# Graph labelsplt.title(‘PMF for an unfair 3-sided die’)     plt.xlabel(‘Number on the face of the die’)     plt.ylabel(‘Probability’)       plt.xticks(b1) </td>

  </tr>

 </tbody>

</table>




<h1>1.     Function for a n-sided die</h1>




Write a function that simulates a single roll of a n-sided die. The inputs and outputs of the function are: <strong>Inputs:</strong>

<ul>

 <li>The probabilities for each side, given as a vector <em>p p p</em>= [ <sub>1</sub>, <sub>2</sub>,L<em>p</em><em><sub>n</sub></em>]</li>

</ul>

<strong>Outputs: </strong>

<ul>

 <li>The number on the face of the die after a single roll, i.e. one number from the set of  integers {1,2,L<em>n</em>}</li>

</ul>

<strong>Note: </strong>The sum <em>p p</em><sub>1 </sub>+ +<sub>2 </sub>L<em>p</em><em><sub>n</sub></em> must be equal to 1.0, otherwise the probability values are incorrect.

<strong>Save</strong>  the function as: nSidedDie(p)




<strong>Test the function</strong> using the probability vector <em>p p p</em>= [ <sub>1</sub>, <sub>2</sub>,L<em>p</em><em><sub>n</sub></em>] which has been  given to you. To create a random number with a single roll of the die you must use the following command:  r=nSidedDie(p)

To validate your function, roll the die for N=10,000 times and plot the outcome as a stem plot.




<strong>SUBMIT a report</strong> that follows the guidelines as described in the syllabus.

Ø The section on RESULTS must include The PMF in the form of a <strong>stem plot</strong>  Ø The code must be provided in the appendix




<h1>2.     Number of rolls needed to get a “7” with two dice</h1>




Consider the following experiment:

<ul>

 <li>You roll a pair of fair dice and calculate the sum of the faces. You are interested in the number of rolls it takes until you get a sum of “7”. The first time you get a “7” the experiment is considered a “success”. You record the number of rolls and you stop the experiment.</li>

 <li>You repeat the experiment N=100,000 times. Each time you keep track of the number of rolls it takes to have “success”.</li>

</ul>




<strong>SUBMIT a report</strong> that follows the guidelines as described in the syllabus.

<ul>

 <li>The section on RESULTS must include The PMF in the form of a <strong>stem plot</strong></li>

 <li>The code must be provided in the appendix</li>

</ul>




<h1>3.     Getting 50 heads when tossing 100 coins</h1>




Consider the following experiment:

<ul>

 <li>You toss 100 fair coins and record the number of “heads”. This is considered a single experiment. If you get exactly 50 heads, the experiment is considered a “success”.</li>

 <li>You repeat the experiment N=100,000 times. After the N experiments are completed count the total successes, and calculate the probability of success, i.e. the probability of getting exactly 50 heads.</li>

</ul>




<strong>SUBMIT a report</strong> that follows the guidelines as described in the syllabus.

<ul>

 <li>The section on RESULTS must include the calculated answer. <em>Use the table below for your answer. </em>Note: You will need to replicate the table in your Word file, in order to provide the answer in your report. Points will be taken off if you do not use the table.</li>

 <li>The code must be provided in the appendix</li>

</ul>




<table width="469">

 <tbody>

  <tr>

   <td width="361">Probability  of 50 heads in tossing 100 fair coins</td>

   <td width="108"> </td>

  </tr>

  <tr>

   <td width="361"><strong>Ans.  </strong></td>

   <td width="108"><strong><em>p =  </em></strong>0.0798</td>

  </tr>

 </tbody>

</table>







<h1>4.     The Password Hacking Problem</h1>




Your computer system uses a 4-letter password for login. For our purposes the password is restricted to lower case letters of the alphabet only.  It is easy to calculate that the total number of passwords which can be produced is <em>n</em>= 26<sup>4</sup>.

<ul>

 <li>A hacker creates a list of  random 4-letter words, as candidates for matching the password. Note that it is possible that some of the  words may be duplicates. The number  that you must use has been given to you.</li>

 <li>You are given your own 4-letter password and you are going to check if the hacker’s list contains at least one word that matches your password. This process of checking  is considered one experiment. If a word in the list matches your password, the experiment is considered a success. Repeat the experiment for <em>N</em>=1000 times and find  the probability that <strong>at least one of the words</strong> in the hacker’s list will match your password.</li>

 <li>The hacker creates a longer list of k* random 4-letter words. The numbers k and  have been given to you. Repeat the previous experiment for</li>

</ul>

<em>N</em>=1000 times and find  the probability that <strong>at least one of the words</strong> in the hacker’s list will match your password.

<ul>

 <li>Repeat the previous experiment for <em>N</em>=1000times to find the <strong>approximate number</strong> (<em>m</em>) of words that must be contained in the hacker’s list so that the probability of at least one word matching the password is</li>

</ul>

<em>p</em>= 0.5. You should do this by trial and error: assume a value for (<em>m</em>) and

calculate the corresponding probability as you did in the previous part. The answer will be value of (<em>m</em>) that makes this probability <strong>approximately equal</strong> to <em>p</em>= 0.5.




<strong>SUBMIT a report</strong> that follows the guidelines as described in the syllabus.

<ul>

 <li>The section on RESULTS must include the calculated answer. <em>Use the table below for your answer. </em>Note: You will need to replicate the table in your Word file, in order to provide the answer in your report. Points will be taken off if you do not use the table.</li>

 <li>The code must be provided in the appendix</li>

</ul>




<table width="540">

 <tbody>

  <tr>

   <td width="414">                                                                              Hacker creates  wordsProb.  that at least one of the words matches the password </td>

   <td width="126"><strong><em> </em></strong><strong><em>p = </em></strong>0.1965</td>

  </tr>

  <tr>

   <td width="414">                                                                         Hacker creates k* wordsProb.  that at least one of the words matches the password </td>

   <td width="126"><strong><em> </em></strong><strong><em>p = </em></strong>0.8879</td>

  </tr>

  <tr>

   <td width="414"><em>p</em>= 0.5Approximate number of words in the list</td>

   <td width="126"><strong><em> </em></strong><strong><em>m = </em></strong>317,000</td>

  </tr>

 </tbody>

</table>




<h1>5.     References</h1>

[1]            “<em>Introduction to Probability</em>,” by H. Pishro-Nik. Available online at:

<a href="https://www.probabilitycourse.com/">https://www.probabilitycourse.com</a>