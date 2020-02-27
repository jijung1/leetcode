* Problem Description 

  On a plane there are n points with integer coordinates points[i] = [xi, yi]. Your task is to find the minimum time in seconds to visit all points.

You can move according to the next rules:

In one second always you can either move vertically, horizontally by one unit or diagonally (it means to move one unit vertically and one unit horizontally in one second).
You have to visit the points in the same order as they appear in the array.

Example 1:

Input: points = [[1,1],[3,4],[-1,0]]
Output: 7
Explanation: One optimal path is [1,1] -> [2,2] -> [3,3] -> [3,4] -> [2,3] -> [1,2] -> [0,1] -> [-1,0]   
Time from [1,1] to [3,4] = 3 seconds 
Time from [3,4] to [-1,0] = 4 seconds
Total time = 7 seconds
Example 2:

Input: points = [[3,2],[-2,2]]
Output: 5
 

Constraints:

points.length == n
1 <= n <= 100
points[i].length == 2
-1000 <= points[i][0], points[i][1] <= 1000

* Solution 

```

 /*
 * @param {number[][]} points
 * @return {number}
 */

var minTimeToVisitAllPoints = function(points) {
    
    //ok so we forgot to consider which direction the nextPoint is relative to currPosition, so let's add that
    
    let elapsedTime = 0;
    let currPosition = [points[0][0],points[0][1]];
    let nextPoint = 1;
    
    while (nextPoint != points.length) {
        //direction to travel from currPosition to nextPoint
        let up = true;
        let right = true;

        if ((points[nextPoint][0] - currPosition[0]) < 0) {
            right = false;
        }
        if ((points[nextPoint][1] - currPosition[1]) < 0) {
            up = false;
        }

        while ((Math.abs(points[nextPoint][0] - currPosition[0]) != 0) && ( Math.abs(points[nextPoint][1] - currPosition[1]) != 0)) {
            elapsedTime++;
            if (up) {
                currPosition[1] +=1;
            }
            else {
                currPosition[1] -=1;
            }
            if (right) {
                currPosition[0] +=1;
            }
            else {
                currPosition[0] -=1;
            }
        }
        while (Math.abs(points[nextPoint][0] - currPosition[0]) != 0) {
            elapsedTime++;
            if (right) {
                currPosition[0] += 1;
            }
            else {
                currPosition[0] -= 1;
            }
        }
        while (Math.abs(points[nextPoint][1] - currPosition[1]) != 0) {
            elapsedTime++;
            if (up) {
                currPosition[1] += 1;
            }
            else {
                currPosition[1] -= 1;
            }
            
        }
                    
        if (currPosition[0] == points[nextPoint][0] && currPosition[1] == points[nextPoint][1]) {
             nextPoint++;
        }
        else {
            console.log("u done fked up");
        }
    }
    console.log(elapsedTime);
    return elapsedTime;
};

```
