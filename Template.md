# 39. Combination Sum
- 39. Combination Sum [Array] [Backtracking] [Medium]

#### Tags
- [Array] [Backtracking] [Medium]

#### Problem
Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

The same repeated number may be chosen from candidates unlimited number of times.

**Note**:

- All numbers (including target) will be positive integers.
- The solution set must not contain duplicate combinations.

Example 1:

    Input: candidates = [2,3,6,7], target = 7,
    A solution set is:
    [
      [7],
      [2,2,3]
    ]
    
Example 2:

    Input: candidates = [2,3,5], target = 8,
    A solution set is:
    [
      [2,2,2,2],
      [2,3,3],
      [3,5]
    ]

#### Solution
``` C++
class Solution {
public:
    vector<vector<int>> combinationSum(
            vector<int> &candidates, int target) {
        vector<vector<int>> results;
        if (candidates.empty() || target <= 0) return results;
        vector<int> temp;
        _combination(candidates, target, 0, temp, results);
        return results;
    }
    
private:
    void _combination(vector<int> &candidates, int target, 
                      int index, vector<int> &temp, 
                      vector<vector<int>> &results) {
        if (target == 0) {
            results.push_back(temp);
            return;
        }
        if (target < 0) return;
        for (int i = index; i < candidates.size(); i++) {
            temp.push_back(candidates[i]);
            _combination(candidates, target - candidates[i], 
                         i, temp, results);
            temp.pop_back();
        }
    }
};
```

#### Time Complexity
- O(n^2)

#### Space Complexity
- O(n)

#### Notes
- Use Recursion, 20180929.

#### Related Problems
- 39. Combination Sum [Array] [Backtracking] [Medium]
- 40. Combination Sum II [Array] [Backtracking] [Medium]
- 216. Combination Sum III [Array] [Backtracking] [Medium]
- 377. Combination Sum IV [Dynamic Programming] [Medium]
- 77. Combinations [Backtracking] [Medium]
- 254. Factor Combinations [Backtracking] [Medium]