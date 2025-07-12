""" SRT BOT
Subproblem: J(i): The minimum number of jumps needed to reach the last platform from platform i
Relation: J(i) = min(J(i+k) + 1) for all k in [1, jumps[i]] if i + k < n
Topological: Decreasing i (from n−1 down to 0)
Base: J(n−1) = 0
Original: J(0)
Time: Θ(n^2)"""

def min_jumps_rec(jumps):
    n = len(jumps)
    memo = {n - 1: 0} 

    def J(i):
        if i in memo:
            return memo[i]
        if jumps[i] == 0:
            memo[i] = float('inf')
            return memo[i]

        min_jumps = float('inf')
        for k in range(1, jumps[i] + 1):
            if i + k < n:
                jump_result = J(i + k)
                if jump_result != float('inf'):
                    min_jumps = min(min_jumps, 1 + jump_result)

        memo[i] = min_jumps
        return memo[i]

    result = J(0)
    return result if result != float('inf') else -1

def min_jumps_iter(jumps):
    n = len(jumps)
    J = [float('inf')] * n
    J[n - 1] = 0 

    for i in reversed(range(n - 1)):
        if jumps[i] > 0:
            for k in range(1, jumps[i] + 1):
                if i + k < n:
                    J[i] = min(J[i], 1 + J[i + k])

    return J[0] if J[0] != float('inf') else -1
