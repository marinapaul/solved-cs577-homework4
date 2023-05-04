Download Link: https://assignmentchef.com/product/solved-cs577-homework4
<br>
<ol>

 <li> Design an algorithm that takes as input two binary sequences <em>a </em>and <em>b </em>of lengths <em>m </em>and <em>n </em>respectively, and outputs the smallest length of a sequence <em>c </em>such that both <em>a </em>and <em>b </em>are subsequences of <em>c</em>. For example, if <em>a </em>= 011 and <em>b </em>= 0101, then the answer is 4, as witnessed by <em>c </em>= 0101. Your algorithm should run in time <em>O</em>(<em>m </em> <em>n</em>).</li>

 <li>Consider the multiplication defined in Table 1. For example, <em>ab </em>= <em>b </em>and <em>ba </em>= <em>c</em>. Note that this multiplication is neither associative nor commutative.</li>

</ol>

Table 1: Multiplication Table

<table width="98">

 <tbody>

  <tr>

   <td width="25"> </td>

   <td width="25">a</td>

   <td width="24">b</td>

   <td width="23">c</td>

  </tr>

  <tr>

   <td width="25">a</td>

   <td width="25">b</td>

   <td width="24">b</td>

   <td width="23">a</td>

  </tr>

  <tr>

   <td width="25">b</td>

   <td width="25">c</td>

   <td width="24">b</td>

   <td width="23">a</td>

  </tr>

  <tr>

   <td width="25">c</td>

   <td width="25">a</td>

   <td width="24">c</td>

   <td width="23">c</td>

  </tr>

 </tbody>

</table>

You want to know, given a string of <em>n </em>symbols <em>a,b,c</em>, with <em>n </em>≥ 1, whether or not it is possible to parenthesize the string in such a way that the value of the resulting expression is <em>a</em>. For example, the string <em>bbbbac </em>can be parenthesized as ((<em>b</em>(<em>bb</em>))(<em>ba</em>))<em>c</em>, and that evaluates to <em>a</em>.

Design an algorithm to solve this problem in time polynomial in <em>n</em>.

<h1>Regular problems</h1>

<ol start="3">

 <li>[Graded, 3 points] A telecommunications company must place <em>n </em>antennas, labeled 1 to <em>n</em>, in <em>k &lt; n </em>separate geographical locations. You’ll be visiting locations 1<em>,…,k </em>in order, once each, to install the antennas. Due to network specs, you can only install antenna <em>i</em>+1 once antenna <em>i </em>has been installed. Still, since <em>k &lt; n</em>, we know some antennas will need to be placed in the same location. The problem is that when we place antennas <em>i </em>and <em>j </em>in the same location, they interfere with intensity <em>s<sub>ij</sub></em>. If we place more than 2 antennas in the same location, then we only need to account for the strongest interference value. For example, if antennas 1, 2 and 3 are in the same location, then the interference in that location has intensity max{<em>s</em><sub>12</sub><em>,s</em><sub>13</sub><em>,s</em><sub>23</sub>}. Given a split of the antennas into the <em>k </em>locations, the total interference is the sum over the maximum interference for each location. We want to determine the minimum total interference that can be realized under the given constraints.</li>

</ol>

More formally, you are given a number <em>k </em>of locations, a number <em>n </em>of antennas, and nonnegative numbers <em>s<sub>ij </sub></em>for every pair of antennas. We need to determine integers 0 ≤ <em>t</em><sub>1 </sub>≤ <em>t</em><sub>2 </sub>≤ <em>… </em>≤ <em>t<sub>k</sub></em><sub>−1 </sub>≤ <em>n </em>(indicating the last antennas placed in locations 1 through <em>k </em>− 1) such that

is minimized, where <em>t</em><sub>0 </sub>= 0 and <em>t<sub>k </sub></em>= <em>n</em>. The max in this expression represents the interference at location <em>i</em>, and we add this value for each location.

For example, consider the instance with <em>k </em>= 2, <em>n </em>= 4, and interference intensities <em>s</em><sub>12 </sub>= 10, <em>s</em><sub>13 </sub>= 5, <em>s</em><sub>14 </sub>= 12, <em>s</em><sub>23 </sub>= 30<em>,s</em><sub>24 </sub>= 40 and <em>s</em><sub>34 </sub>= 15. Observe that there are 5 possible ways to split the 4 antennas into the 2 locations:

<ul>

 <li>Split 1: {}{1<em>,</em>2<em>,</em>3<em>,</em>4}</li>

 <li>Split 2: {1}{2<em>,</em>3<em>,</em>4}</li>

 <li>Split 3: {1<em>,</em>2}{3<em>,</em>4}</li>

 <li>Split 4: {1<em>,</em>2<em>,</em>3}{4}</li>

 <li>Split 5: {1<em>,</em>2<em>,</em>3<em>,</em>4}{}</li>

</ul>

The first and last ones are equivalent and have a total interference value of 40. Split 2 also has total interference 40, while Split 3 has total interference 10 + 15 = 25 and split 4 has total interference 30. In this case, the answer is 25. Note that if we could change the order of the antennas, the total interference could be reduced even further (laction 1 contains {1<em>,</em>3<em>,</em>4} and location 2 contains {2}, for a total interference value of 15), but this is not allowed.

<ul>

 <li>Design an <em>O</em>(<em>n</em><sup>2</sup>) algorithm that outputs the maximum interference values for the subinstances consisting of antennas <em>i </em>through <em>j </em>for <em>all </em>1 ≤ <em>i </em>≤ <em>j </em>≤ <em>n </em>and <em>k </em>= 1.</li>

 <li>Design an <em>O</em>(<em>kn</em><sup>2</sup>) algorithm to solve the problem for a given instance with <em>n </em>antennas and a given <em>k</em>. Your algorithm should output the minimum total interference that can be realized under the constraints.</li>

</ul>

<ol start="4">

 <li>In modern origami (the Japanese art of paper folding), one typically starts with a square sheet of paper and attempts to transform this square into a three-dimensional animal, geometric object, or any other sculpture one can think of, using nothing but a sequence of folds. In traditional 17th–18th century origami, however, the starting shape of the paper was less strictly prescribed.</li>

</ol>

Hiro has stumbled across a book containing instructions for <em>n </em>origami sculptures from this early period, each of which starts from rectangular paper of size <em>a<sub>i </sub></em>× <em>b<sub>i </sub></em>where <em>a<sub>i </sub></em>and <em>b<sub>i </sub></em>are positive integers. He would like to make a diorama containing as many of these (not necessarily distinct) sculptures as possible, but he only has access to a single sheet of paper of size <em>A</em>×<em>B </em>(where <em>A </em>and <em>B </em>are also positive integers) and no scissors. By folding the paper carefully and tearing along the crease, Hiro is confident that he can make perfect horizontal and vertical cuts across an entire sheet of paper, splitting the sheet into two.

Design an algorithm that on input <em>A,B,a</em><sub>1</sub><em>,…,a<sub>n</sub>,b</em><sub>1</sub><em>,…,b<sub>n</sub></em>, computes the maximum number of sculptures that can be made from the starting sheet of paper. Your algorithm should run in time polynomial in <em>A</em>, <em>B</em>, and <em>n</em>.

<ol start="5">

 <li>Gerrymandering is the practice of carving up electoral districts in very careful ways so as to lead to outcomes that favor a particular political party. Recent court challenges to the practice have argued that through this calculated redistricting, large numbers of voters are being effectively (and intentionally) disenfranchised.</li>

</ol>

Computers, as it turns out, have been implicated as some of the main “villains” in much of the news coverage on this topic: it is only thanks to powerful software that gerrymandering grew from an activity carried out by a bunch of people with maps, pencil, and paper into the industrial-strength process it is today. Why is gerrymandering a computational problem? Partly it is the database issues involved in tracking voter demographics down to the level of individual streets and houses; and partly it is the algorithmic issues involved in grouping voters into districts. Let’s think a bit about what these latter issues look like.

Suppose we have a set of precincts <em>P</em><sub>1</sub><em>,P</em><sub>2</sub><em>,…,P<sub>n</sub></em>, each containing <em>m </em>registered voters. We’re supposed to group these precincts into two districts, each consisting of <em>n/</em>2 of the precincts. Now, for each precinct, we have information on how many voters are registered to each of two political parties. (Suppose for simplicity that every voter is registered to one of these two.) We say that the set of precincts is susceptible to gerrymandering if it is possible to perform the division in such a way that the same party holds a majority in both districts.

Design an algorithm to determine whether a given set of precincts is susceptible to gerrymandering. The running time of your algorithm should be polynomial in <em>n </em>and <em>m</em>.

<strong>Example </strong>Suppose we have <em>n </em>= 4 precincts, and the following information on registered voters. Party A has 55, 43, 60, and 47 voters in districts <em>P</em><sub>1</sub><em>,P</em><sub>2</sub><em>,P</em><sub>3</sub><em>,P</em><sub>4 </sub>respectively, and party B has 45, 57, 40, and 53. This set of precincts is susceptible, since if we grouped precincts <em>P</em><sub>1 </sub>and <em>P</em><sub>4 </sub>into one district, and precincts <em>P</em><sub>2 </sub>and <em>P</em><sub>3 </sub>into the other, then party A would have a majority in both districts. (Presumably, the “we” who are doing the grouping here are members of party A.) This example is a quick illustration of the basic unfairness in gerrymandering: although party A holds only a slim majority in the overall population (205 to 195), it ends up with a majority in not one but both districts.

<h1>Challenge problem</h1>

<ol start="6">

 <li>Consider problem 3, but with the modification that the interference at a location with more than 2 antennas is the sum of the pairwise interference values instead of the maximum. That is, if antennas 1, 2 and 3 are in the same location, then the interference in that location has intensity <em>s</em><sub>12 </sub>+<em>s</em><sub>13 </sub>+<em>s</em><sub>23</sub>. Again, we want to minimize the total interference over all locations.</li>

</ol>

<ul>

 <li>Design an <em>O</em>(<em>n</em><sup>2</sup>) algorithm that outputs the interference values for the subinstance consisting of antennas <em>i </em>through <em>j </em>for <em>all </em>1 ≤ <em>i </em>≤ <em>j </em>≤ <em>n </em>and <em>k </em>= 1.</li>

 <li>Design an <em>O</em>(<em>kn</em>log<em>n</em>) algorithm to solve the problem for a given instance with <em>n </em>antennas and a given <em>k </em>when given access to the one-location interference values computed in part (a). Your algorithm should output the minimum total interference that can be realized under the constraints.</li>

</ul>

<h1>Programming problem</h1>

<ol start="7">

 <li>SPOJ problem <a href="https://www.spoj.com/problems/SQRBR">Square Brackets</a> (problem code SQRBR).</li>

</ol>