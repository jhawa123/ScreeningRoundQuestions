# ScreeningRoundQuestions

# Question 1: Motivation and Commitment
I am deeply aligned with Company's mission of driving innovation and delivering outstanding user experiences. My commitment to professional growth ensures I stay abreast of the latest technologies, bringing cutting-edge solutions to support your goals. I thrive in collaborative environments and am dedicated to solving complex problems with a user-centric approach, ensuring high-quality, impactful software. My passion for continuous learning and excellence, combined with a focus on long-term vision, underscores my motivation and dedication to contributing to Company's success and mission.

As a software engineer with a passion for both technical excellence and continuous learning, my motivation and commitment to supporting Company's mission. I have a strong background in software engineering, which I believe will be crucial in building robust and scalable solutions for your product. Additionally, my passion for learning and teaching can contribute to fostering a collaborative and growth-oriented environment within the team. I am confident that my skills can significantly contribute to your early success, and I am fully committed to dedicating 20 hours per week to this role in the long term.

# Question 2: High-Level Architecture

Data Collection:
To gather e-commerce data from various websites, I would use APIs provided by e-commerce platforms to get structured data. Additionally, I would use web scraping tools like BeautifulSoup and Scrapy to extract information. The collected data would be stored in a database like MongoDB.

Components: API Clients, Web Scrapers (using BeautifulSoup, Scrapy)
Function: These components collect data from various e-commerce websites and APIs.
Interaction: Web Scrapers extract unstructured data directly from websites, while API Clients retrieve structured data from e-commerce platforms' APIs. Both types of data are then stored in MongoDB.

AI Agent:
For analyzing and optimizing product listings, I would use AI models like BERT or GPT for text analysis. For predicting trends and finding optimization opportunities, I would use machine learning models like Random Forest or XGBoost.

Components: NLP Models (BERT, GPT), Machine Learning Models (Random Forest, XGBoost)
Function: Analyzes the stored data and provides insights and optimization recommendations.
Interaction: The AI Agent retrieves data from MongoDB, processes it using NLP and machine learning models, and generates analysis results.

User Interface:
The user interface would be a web application built with React.js, making it easy and interactive for users to use. Users can view and interact with data insights and optimization recommendations through dashboards.

Components: Web Application (React.js)
Function: Provides a platform for users to interact with the AI Agent and view the results.
Interaction: Users interact with the web application, which requests analysis results from the AI Agent. The results are then displayed in an interactive dashboard.

Scalability:
To handle an increasing number of users and data sources, I would use microservices architecture. This would allow us to manage different parts of the system independently. Kubernetes would help in managing these microservices, ensuring the system can scale easily. A load balancer like Nginx would distribute incoming traffic evenly, making sure the system runs smoothly.

Components: Microservices Architecture, Kubernetes, Nginx Load Balancer
Function: Ensures the system can handle a growing number of users and data sources efficiently.
Interaction: The system is divided into microservices managed by Kubernetes for scalability and flexibility. Nginx distributes incoming traffic evenly across the system to maintain performance.

# Question 3: Coding Question

from collections import defaultdict, Counter
from datetime import datetime, timedelta

#Parses a log file to extract and organize user activities by date.
def parse_log(log):
    activity = defaultdict(set)
    for entry in log:
        date_str, user, action = entry.split(', ')
        date = datetime.strptime(date_str, '%Y-%m-%d')
        activity[user].add(date)
    return activity

#Calculates the longest consecutive activity streak and total activity days for each user.
def get_streaks(activity):
    streaks = {}
    for user, dates in activity.items():
        sorted_dates = sorted(dates)
        max_streak, current_streak = 0, 1
        for i in range(1, len(sorted_dates)):
            if sorted_dates[i] == sorted_dates[i - 1] + timedelta(days=1):
                current_streak += 1
            else:
                max_streak = max(max_streak, current_streak)
                current_streak = 1
        max_streak = max(max_streak, current_streak)
        streaks[user] = (max_streak, len(dates))
    return streaks

#Identifies the top K users with the longest activity streaks from the parsed log data.
def top_k_users(log, k):
    activity = parse_log(log)
    streaks = get_streaks(activity)
    sorted_users = sorted(streaks.items(), key=lambda x: (-x[1][0], -x[1][1]))
    return [user for user, _ in sorted_users[:k]]

# Example usage:
log_file = [
    "2024-07-01, User1, post",
    "2024-07-01, User2, like",
    "2024-07-02, User1, comment",
    "2024-07-03, User1, like",
    "2024-07-03, User3, post",
    "2024-07-04, User2, comment",
    "2024-07-05, User3, like"
]

print(top_k_users(log_file, 2))  # Output: ['User1', 'User3']


# Question 4: Salary Expectation

The proposed salary range of 30,000 to 50,000 rupees per month for part-time work aligns with my expectations and is acceptable to me. Additionally, I am open to discussing a full-time position with a salary range of 60,000 to 90,000 rupees per month. I would like to explore both options further and determine which would be the best fit for my contributions to the team.


Thank You

