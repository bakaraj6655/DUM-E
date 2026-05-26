# DUM'E — Chess Session Recorder
### v1.1 | Project by Kaju

> Named after Tony Stark's clumsy but loyal robot arm.
> DUM'E records your chess games, learning logs, and helps Jarvis (Claude) analyze your improvement.

---

## Stack
- Frontend: Vanilla HTML/CSS/JS
- AI: Gemini 2.0 Flash (free tier)
- Database: Supabase (free tier)
- Hosting: Vercel (free tier)

## Setup

### 1. Supabase — run this SQL in your SQL Editor:

```sql
create table games (
  id uuid default gen_random_uuid() primary key,
  created_at timestamp with time zone default now(),
  player text,
  color text,
  result text,
  game_type text,
  opponent_rating integer,
  opening_played text,
  mental_state text,
  kaju_thoughts text,
  turning_point text,
  blunder_moment text,
  opponent_surprise text,
  error_CAGE boolean default false,
  error_CAGE_detail text
);

create table learn_logs (
  id uuid default gen_random_uuid() primary key,
  created_at timestamp with time zone default now(),
  player text,
  summary text,
  topics text[]
);

alter table games enable row level security;
alter table learn_logs enable row level security;

create policy "allow all" on games for all using (true) with check (true);
create policy "allow all" on learn_logs for all using (true) with check (true);
```

### 2. Fill in your keys in `public/index.html`:
- Line with `SUPABASE_URL_HERE` → your Supabase project URL
- Line with `SUPABASE_ANON_KEY_HERE` → your Supabase anon public key
- Line with `GEMINI_API_KEY_HERE` → your Gemini API key

### 3. Push to GitHub and deploy on Vercel.

---

## Roadmap
- [x] v1.0 — Basic game diary
- [x] v1.1 — Learning log, Supabase persistence, Vercel deployment, mobile ready
- [ ] v1.2 — PGN paste, post-game interview, enriched JSON
- [ ] v1.3 — Screenshot upload, image reading

---

*Built with Claude (Jarvis). Second project by Kaju.*
