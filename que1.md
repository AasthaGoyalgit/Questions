# Title

[![Problem Link](../assets/gfg.svg)](https://practice.geeksforgeeks.org/problems/print-anagrams-together/1/#)
<!-- [![Problem Link](../assets/lc.svg)](link) -->


### Sample Input
```
N = 5
words[] = {act,god,cat,dog,tac}

```
### Sample Output
```
act cat tac 
god dog

```

### Solution
```Java
class Solution {
    public List<List<String>> Anagrams(String[] words) {
        // Code here
        int n = words.length;
        HashMap< HashMap<Character, Integer> , List<String>> hm = new HashMap<>();
		List<List<String>>  ans = new ArrayList<>();
		
		for(int i=0; i<n; i++) {
			HashMap<Character, Integer> interHm = fillHashMap(words[i]);
			if(hm.containsKey(interHm)) {
				List<String> temp = hm.get(interHm);
				temp.add(words[i]);
				hm.put(interHm, temp);
			}
			else {
				List<String> temp = new ArrayList<>();
				temp.add(words[i]);
				hm.put(interHm, temp);
			}
		}
		
		for(List val: hm.values()) {
			ans.add(val);
		}
		
		
		
		return ans;
        
    }
    
    public HashMap<Character, Integer> fillHashMap(String s) {
		HashMap<Character, Integer> interHm = new HashMap<>();
		
		for(int i=0; i<s.length(); i++) {
			char ch = s.charAt(i);
			interHm.put(ch , interHm.getOrDefault(ch,0)+1);
		}
		
		return interHm;
	}
}

```

### Accepted
[![image](https://user-images.githubusercontent.com/66162540/167266455-d98bf5ae-b3cd-441c-b2dd-e785749c02ce.png)](https://practice.geeksforgeeks.org/viewSol.php?subId=6497d795394d31c2822e6b3cc7980570&pid=701966&user=aasthagoyal820)