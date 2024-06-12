# [PROPOSAL-002] Guru Network Token Distribution Between Core Contributors

## Introduction

This proposal outlines an algorithm for distributing tokens among DAO members based on their contributions and the importance of their roles. The goal is to ensure a fair and transparent method for rewarding members based on their efforts and impact.

## Overview

The algorithm considers both individual contributions and role importance, using predefined weights to calculate each member's share of the total tokens. This method ensures that both the quantity and quality of work are recognized, as well as the varying significance of different roles within the organization.

## Methodology

### Weights for Roles and Metrics

To achieve a balanced distribution, we will assign specific weights to different roles and metrics. These weights can be adjusted based on the organization's priorities and goals.

#### Role Weights

| Role       | Weight |
|------------|--------|
| Developer  | 1.0    |
| Marketer   | 0.8    |
| Designer   | 0.9    |
| DevOps     | 1.1    |

#### Metric Weights

| Metric            | Weight |
|-------------------|--------|
| Tasks Completed   | 0.3    |
| Time Efficiency   | 0.2    |
| Task Complexity   | 0.2    |
| Quality of Work   | 0.3    |

### Evaluation of Individual Contributions

Each member's contribution will be evaluated based on the following metrics:

- **Tasks Completed:** Number of tasks completed during the period.
- **Time Efficiency:** How efficiently the tasks were completed.
- **Task Complexity:** Complexity of the tasks undertaken.
- **Quality of Work:** Quality of the work produced.

### Calculation of Weighted Contributions

The algorithm calculates the weighted contributions by combining the role and metric weights with individual performance data. This ensures that both the role's importance and the member's personal achievements are considered.

### Token Distribution Process

1. **Define Weights for Roles and Metrics:**
   ```python
   role_weights = {
       'developer': 1.0,
       'marketer': 0.8,
       'designer': 0.9,
       'devops': 1.1
   }

   metric_weights = {
       'tasks_completed': 0.3,
       'time_efficiency': 0.2,
       'task_complexity': 0.2,
       'quality_of_work': 0.3
   }
   ```

2. **Evaluate Members' Contributions:**
   ```python
   contributions = {
       'Alice': {
           'role': 'developer',
           'metrics': {
               'tasks_completed': 80,
               'time_efficiency': 75,
               'task_complexity': 70,
               'quality_of_work': 85
           }
       },
       'Bob': {
           'role': 'developer',
           'metrics': {
               'tasks_completed': 70,
               'time_efficiency': 80,
               'task_complexity': 75,
               'quality_of_work': 80
           }
       },
       # And so on for other members
   }
   ```

3. **Calculate Weighted Contributions:**
   ```python
   def calculate_weighted_contribution(contributions, role_weights, metric_weights):
       weighted_contributions = {}
       total_weighted_contribution = 0

       for name, info in contributions.items():
           role = info['role']
           metrics = info['metrics']
           role_weight = role_weights[role]
           
           weighted_sum = 0
           for metric, value in metrics.items():
               weighted_sum += value * metric_weights[metric]
           
           weighted_contribution = weighted_sum * role_weight
           weighted_contributions[name] = weighted_contribution
           total_weighted_contribution += weighted_contribution

       return weighted_contributions, total_weighted_contribution

   weighted_contributions, total_weighted_contribution = calculate_weighted_contribution(contributions, role_weights, metric_weights)
   ```

4. **Distribute Tokens:**
   ```python
   total_tokens = 50000000
   token_distribution = {}

   for name, weighted_contribution in weighted_contributions.items():
       share = weighted_contribution / total_weighted_contribution
       token_distribution[name] = share * total_tokens

   # Print token distribution
   for name, tokens in token_distribution.items():
       print(f'{name} receives {tokens} tokens')
   ```

### Full Code

```python
# Define weights for roles
role_weights = {
    'developer': 1.0,
    'marketer': 0.8,
    'designer': 0.9,
    'devops': 1.1
}

# Define weights for metrics
metric_weights = {
    'tasks_completed': 0.3,
    'time_efficiency': 0.2,
    'task_complexity': 0.2,
    'quality_of_work': 0.3
}

# Members' contributions by metrics
contributions = {
    'Alice': {
        'role': 'developer',
        'metrics': {
            'tasks_completed': 80,
            'time_efficiency': 75,
            'task_complexity': 70,
            'quality_of_work': 85
        }
    },
    'Bob': {
        'role': 'developer',
        'metrics': {
            'tasks_completed': 70,
            'time_efficiency': 80,
            'task_complexity': 75,
            'quality_of_work': 80
        }
    },
    'Charlie': {
        'role': 'developer',
        'metrics': {
            'tasks_completed': 60,
            'time_efficiency': 70,
            'task_complexity': 65,
            'quality_of_work': 75
        }
    },
    'Dave': {
        'role': 'developer',
        'metrics': {
            'tasks_completed': 85,
            'time_efficiency': 85,
            'task_complexity': 80,
            'quality_of_work': 90
        }
    },
    'Eve': {
        'role': 'developer',
        'metrics': {
            'tasks_completed': 55,
            'time_efficiency': 60,
            'task_complexity': 65,
            'quality_of_work': 70
        }
    },
    'Frank': {
        'role': 'developer',
        'metrics': {
            'tasks_completed': 65,
            'time_efficiency': 70,
            'task_complexity': 75,
            'quality_of_work': 80
        }
    },
    'Grace': {
        'role': 'developer',
        'metrics': {
            'tasks_completed': 75,
            'time_efficiency': 80,
            'task_complexity': 85,
            'quality_of_work': 90
        }
    },
    'Heidi': {
        'role': 'marketer',
        'metrics': {
            'tasks_completed': 90,
            'time_efficiency': 85,
            'task_complexity': 80,
            'quality_of_work': 90
        }
    },
    'Ivan': {
        'role': 'designer',
        'metrics': {
            'tasks_completed': 85,
            'time_efficiency': 80,
            'task_complexity': 75,
            'quality_of_work': 85
        }
    },
    'Judy': {
        'role': 'devops',
        'metrics': {
            'tasks_completed': 95,
            'time_efficiency': 90,
            'task_complexity': 85,
            'quality_of_work': 95
        }
    }
}

# Function to calculate weighted contributions
def calculate_weighted_contribution(contributions, role_weights, metric_weights):
    weighted_contributions = {}
    total_weighted_contribution = 0

    for name, info in contributions.items():
        role = info['role']
        metrics = info['metrics']
        role_weight = role_weights[role]
        
        weighted_sum = 0
        for metric, value in metrics.items():
            weighted_sum += value * metric_weights[metric]
        
        weighted_contribution = weighted_sum * role_weight
        weighted_contributions[name] = weighted_contribution
        total_weighted_contribution += weighted_contribution

    return weighted_contributions, total_weighted_contribution

# Calculate weighted contributions
weighted_contributions, total_weighted_contribution = calculate_weighted_contribution(contributions, role_weights, metric_weights)

# Token distribution
total_tokens = 50000000
token_distribution = {}

for name, weighted_contribution in weighted_contributions.items():
    share = weighted_contribution / total_weighted_contribution
    token_distribution[name] = share * total_tokens

# Print token distribution
for name, tokens in token_distribution.items():
    print(f'{name} receives {tokens} tokens')
```
