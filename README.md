# Codility-Jurassic-Code
Given a set of points on a plane, find the largest number of points that can be enclosed within a circle centered on the origin, such that the number of red points and green points inside it is equal.

# Task description
There are N points (numbered from 0 to N−1) on a plane. Each point is colored either red ('R') or green ('G'). The K-th point is located at coordinates (X[K], Y[K]) and its color is colors[K]. No point lies on coordinates (0, 0).

We want to draw a circle centered on coordinates (0, 0), such that the number of red points and green points inside the circle is equal. What is the maximum number of points that can lie inside such a circle? Note that it is always possible to draw a circle with no points inside.

# Link Details
[https://app.codility.com/cert/view/certCQDNQB-YPUGAVGA7D7ZR75N/details/](https://app.codility.com/cert/view/certCQDNQB-YPUGAVGA7D7ZR75N/details/)

# Programming Language
Java SE 8

# Solution Code

```
import java.util.*;

class Solution 
{
      public int solution(int[] X, int[] Y, String colors) 
      {
        List<Double> distanceList = new ArrayList<Double>(X.length);
        List<Integer> noList = new ArrayList<Integer>(X.length);
        noList.add(0);
        int noR=0, noG=0;
       
        String[] strSplit = colors.split("");
  
        // Now convert string into ArrayList
        List<String> colorList = new ArrayList<String>(
            Arrays.asList(strSplit));

        if(!colorList.contains("R") || !colorList.contains("G")){
            return 0;
        }

        for(int i=0;i<X.length;i++){
            distanceList.add(Math.round(distance(0, 0, X[i], Y[i]) *100000.0)/ 100000.0);
        }
         for(int i=0;i<distanceList.size();i++){
             double node=distanceList.get(i);
            for(int j=0;j<distanceList.size();j++){
                if(node>distanceList.get(j) || node==distanceList.get(j)){
                    // System.out.println(j+ ":"+ colorList.get(j));
                if(colorList.get(j).equals("R")){
                    noR++;
                }
                else if(colorList.get(j).equals("G")){
                    noG++;
                }
            }
        
        }
        if(noR==noG){
            noList.add(noG+noR);
        } 
        noG=0;
        noR=0;                
    }       
        return Collections.max(noList);

    }

    static double distance(int x1, int y1, int x2, int y2)
    {
        // Calculating distance
        return Math.sqrt(Math.pow(x2 - x1, 2)
                         + Math.pow(y2 - y1, 2) * 1.0);
    }
}
```
