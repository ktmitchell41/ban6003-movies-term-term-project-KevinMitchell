# Movies Project Data Guide

The provided files have different row meanings. Check keys before joining and keep the final ABT unit explicit.

| File | One row represents | Expected key | Integration note |
|---|---|---|---|
| `movies_metadata.csv` | One movie in the curated catalog | `movieId`; `tmdbId` is also expected to identify one curated movie | Recommended base table for a one-row-per-movie ABT |
| `ratings.csv` | One user's rating event for one movie | `userId` + `movieId` | Aggregate to `movieId` before joining a movie-level ABT |
| `links.csv` | One MovieLens movie ID crosswalk | `movieId` | Use to validate or supply MovieLens, IMDb, and TMDB ID mappings |
| `credits_curated.csv` | Curated director and top-cast fields for one TMDB movie | `tmdbId` | Join only after checking `tmdbId` uniqueness |
| `keywords_curated.csv` | Curated keyword text for one TMDB movie | `tmdbId` | Join only after checking `tmdbId` uniqueness |

Important target note: the starter defines `high_user_rating` only when a movie has at least 20 user ratings. Movies below that evidence threshold have an undefined target, represented as a missing value rather than class 0.

For pre-release prediction questions, do not use post-release fields such as observed revenue, popularity, vote counts, rating summaries, or rating dates as predictors.

Movie Box Office Success Project
 
Objective
This project analyzes movie attributes associated with box office revenue to determine possible connections between movie data/characteristics and profitability.
 
Data Sources
- movies_metadata.csv
- ratings.csv
- credits_curated.csv
- keywords_curated.csv
- links.csv
 
Repository Structure
- data/ contains raw datasets
- notebooks/ contains analysis notebooks
- reports/ contains project deliverables
 
Reproduction Instructions
1. Open the notebook in notebooks.
2. Run all cells from top to bottom.
3. Data files are located in the directory.