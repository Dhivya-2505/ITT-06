class Solution {
public:
    int romanToInt(string s) {
        // 1. Map symbols to values
        unordered_map<char, int> values = {
            {'I', 1},   {'V', 5},   {'X', 10}, 
            {'L', 50},  {'C', 100}, {'D', 500}, {'M', 1000}
        };
        
        int total = 0;
        int n = s.length();

        for (int i = 0; i < n; i++) {
            // 2. Check if this is a subtraction case
            // If current value < next value, subtract it
            if (i < n - 1 && values[s[i]] < values[s[i + 1]]) {
                total -= values[s[i]];
            } 
            // 3. Otherwise, just add it
            else {
                total += values[s[i]];
            }
        }

        return total;
    }
};
