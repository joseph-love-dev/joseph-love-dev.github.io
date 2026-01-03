---
layout: project
title: "Ball Knowledge"
date: "Mar 2025 - Present"
subtitle: "AI Fantasy Football Chatbot"
permalink: /projects/fantasy-points/
back_link: "/#experience"
back_text: "Back to Experience"
---

Since Ball Knowledge is locked behind a paywall, I figured I would write a bit more to explain more about the project. I cannot go into complete detail about the stack (it is a paid FantasyPoints product after all), but my goal is to give some more insight on my ability to build something real and production grade.


## What is it?

Ball Knowledge is an AI chatbot that understands fantasy football better than ChatGPT or any other LLM. It is powered by FantasyPoints data, articles, and rankings (hence the URL being www.fantasypoints.ai). Users ask questions and get real-time statistics, visualizations, and fantasy insights. This entire project was built and deployed to production in roughly 5 months, however, I still actively work on it and add more features every week.

## Backend

There are two Python APIs that I built from scratch in the backend that I want to focus on. Both APIs are built with FastAPI and deployed on Railway.

The first one deals with all the FantasyPoints data, which includes player projections, fantasy football data, player rankings, draft information, article content, and much more. This API is probably the part of the project that I am most proud of. I implemented a RAG pipeline with semantic search and reranking for referencing articles, built automated data pipelines to process and refresh large datasets, and used a fuzzy matching system for player name resolution.

The second backend API deals with historical player statistics, such as yards, touchdowns, interceptions, etc. This data goes back 25 years, meaning that we store 20+ million data points. Sorting through all this data efficiently proved to be a massive undertaking, however, if you use Ball Knowledge you can get a response in less than 10 seconds on most queries. I don't want to go into detail on how this was accomplished since some competitors are having issues with this challenge.

## Frontend

The frontend is Next.js and I integrated AI using Vercel AI SDK. The UI uses Tailwind CSS, shadcn/ui, and some custom visuals. One of the challenges of building this was integrating it with FantasyPoints' existing user base. I had to learn the basics of Firebase Auth and connect it with NextAuth.js to handle authentication and role-based access control to different subscription tiers unlock different features.

The AI integration was particularly interesting to build. I created a modular tool system where the AI dynamically decides which backend APIs to call based on the user's question, then streams the response back in real-time. For data-heavy responses, I built custom components: player cards, stat leaderboards, and charts using Recharts that render inline with the AI's text response.

The app uses React Server Components for fast initial page loads and Drizzle ORM with Neon Postgres for storing chat history and user data.

## Showcase

In this section I am going to share some images of the tool along with some shareable links that show you the conversation.

### Visuals

Ball Knowledge has custom visuals that are used to better represent player data. Creating these visuals has been fun for me and I keep finding myself adding more and more. I built these with Recharts for charts and custom React components for player cards and leaderboards. Each visualization type renders dynamically based on what the AI's response contains.

**Line Graph** - Below is a line graph that is used to compare weekly player data. The AI has the ability to choose which data is being represented. The "Fantasy Points", "Total Yards", and "Opportunities" tabs are clickable and will dynamically change the view.

<div class="showcase-item">
  <img src="/assets/images/fantasy-points/chart_comp.jpeg" alt="Line graph comparing weekly player data">
</div>

**Bar Graph** - Similar to the line graph, the bar graph is used to compare player statistics along with yearly comparisons.

<div class="showcase-item">
  <img src="/assets/images/fantasy-points/bar_graph_comp.jpeg" alt="Bar graph comparing player statistics">
</div>

**Trade Analyzer** - The trade analyzer tool automatically builds a table that breaks down the values of both sides of a trade. Since this visual is generated automatically, it renders immediately after the trade tool is called.

<div class="showcase-item">
  <img src="/assets/images/fantasy-points/trade_analyzer.jpeg" alt="Trade analyzer breakdown table">
</div>

### League Sync

One of the more recent features I have added is league sync. Users can automatically sync their fantasy teams to Ball Knowledge, allowing them to get personalized insights such as optimal lineups and trade suggestions. This involved integrating with external fantasy platform APIs and storing roster data to give the AI personalized context. The image shows the league sync settings, where users can connect as many teams as they would like. Below is a link to a chat giving me suggestions on who to start for week 17, I ended up winning the championship because of these insights!

<div class="showcase-item">
  <img src="/assets/images/fantasy-points/league_sync.png" alt="League sync settings">
</div>

<a href="https://www.fantasypoints.ai/chat/a9cca116-edc6-4dbc-8087-89de55040d5a" target="_blank" rel="noopener noreferrer" class="showcase-link">View example chat: Week 17 start/sit suggestions</a>
