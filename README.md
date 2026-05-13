# Skill Autofill System

> AI-powered Career Optimization Platform - 100% Rule-Based (No Paid AI APIs)

An intelligent system that analyzes job descriptions and user profiles to provide skill gap analysis, personalized learning roadmaps, resume improvements, and more.

## 🎯 Features

- **Job Description Analysis** - Extract structured data from any job posting
- **Profile Analysis** - Parse resumes and GitHub profiles to identify skills
- **Skill Gap Analysis** - Compare your skills against job requirements
- **Learning Roadmap** - Week-by-week learning plans with resources
- **Resume Optimization** - ATS-safe bullet point improvements
- **Project Suggestions** - Portfolio projects aligned with job requirements
- **GitHub Integration** - Auto-generate issues for learning tasks
- **Portfolio Updates** - Skill and content recommendations

## 🛠️ Tech Stack

- **Frontend**: Next.js 14 (App Router), TypeScript, Tailwind CSS
- **Backend**: Node.js API Routes
- **Database**: Supabase (PostgreSQL, Auth, Storage)
- **NLP**: Rule-based extraction with keyword matching and skill taxonomy
- **Integrations**: GitHub API (public endpoints)

## 📁 Project Structure

```
src/
├── app/                    # Next.js App Router
│   ├── api/               # API routes
│   │   ├── extract-jd/    # Job description extraction
│   │   ├── analyze-profile/ # Profile analysis
│   │   ├── skill-gap/     # Skill gap analysis
│   │   ├── generate-roadmap/ # Roadmap generation
│   │   ├── generate-all/  # Complete pipeline
│   │   ├── apply-updates/ # Apply changes
│   │   └── github/        # GitHub integration
│   ├── about/             # About page
│   ├── docs/              # API documentation
│   ├── history/           # Analysis history
│   ├── layout.tsx         # Root layout
│   ├── page.tsx           # Home page
│   └── globals.css        # Global styles
├── components/            # React components
│   ├── ui/               # Reusable UI components
│   ├── modals/           # Modal components
│   ├── results/          # Result display cards
│   ├── Header.tsx        # Navigation header
│   ├── JDInput.tsx       # Job description input
│   ├── ProfileInput.tsx  # Resume/GitHub input
│   ├── LoadingState.tsx  # Loading indicators
│   └── AnalysisResults.tsx # Results container
├── hooks/                 # Custom React hooks
│   ├── useAnalysis.ts    # Analysis state management
│   └── useLocalStorage.ts # Persistent storage
├── lib/                   # Core libraries
│   ├── nlp/              # NLP processing modules
│   │   ├── skill-taxonomy.ts  # Skill normalization
│   │   ├── jd-extractor.ts    # JD parsing
│   │   ├── profile-analyzer.ts # Profile parsing
│   │   ├── skill-gap-engine.ts # Gap analysis
│   │   ├── roadmap-generator.ts # Learning plans
│   │   ├── resume-improver.ts  # Resume optimization
│   │   ├── project-recommender.ts # Project suggestions
│   │   ├── github-task-generator.ts # GitHub issues
│   │   └── portfolio-updater.ts # Portfolio updates
│   ├── supabase/         # Supabase client
│   └── utils.ts          # Utility functions
├── services/             # API services
│   ├── api.ts           # API client
│   └── github.ts        # GitHub API client
└── types/                # TypeScript definitions
    └── index.ts         # All type definitions
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn
- Supabase account

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/skill-autofill-system.git
   cd skill-autofill-system
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.local.example .env.local
   ```
   
   Edit `.env.local` with your credentials:
   ```
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
   SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
   GITHUB_TOKEN=your_github_token  # Optional, for higher rate limits
   ```

4. **Set up the database**
   ```bash
   # Run migrations in Supabase SQL Editor
   # Copy contents of supabase/migrations/001_initial_schema.sql
   ```

5. **Start development server**
   ```bash
   npm run dev
   ```

6. **Open in browser**
   ```
   http://localhost:3000
   ```

## 📖 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/extract-jd` | Extract structured data from job description |
| POST | `/api/analyze-profile` | Analyze resume and GitHub profile |
| POST | `/api/skill-gap` | Compare skills against job requirements |
| POST | `/api/generate-roadmap` | Generate learning roadmap |
| POST | `/api/generate-all` | Run complete analysis pipeline |
| POST | `/api/apply-updates` | Apply changes to GitHub/portfolio |
| POST | `/api/github/create-issues` | Create GitHub issues |
| GET | `/api/github/profile` | Fetch GitHub profile data |

## 🧠 How It Works (No AI APIs!)

This system uses **100% rule-based NLP** techniques:

### 1. Skill Taxonomy
- Predefined dictionary of 100+ skills with aliases
- Category classification (language, framework, tool, etc.)
- Canonical name normalization

### 2. Keyword Extraction
- Regex patterns for skill detection
- TF-IDF scoring for keyword importance
- Section-based parsing (requirements, responsibilities)

### 3. Priority Scoring
```
Priority = (Frequency × 2) + (Section Weight × 3) + (Required Flag × 5)
- High: score > 15
- Medium: score > 8
- Low: score <= 8
```

### 4. ATS Optimization
- Action verb patterns
- Quantifiable metrics detection
- Keyword density calculation
- Industry-safe rewrites

## 🔒 Privacy & Security

- ✅ No data sent to external AI APIs
- ✅ Resume data processed server-side only
- ✅ No permanent storage without user account
- ✅ GitHub uses public API only
- ✅ Supabase RLS for data isolation

## 🎨 UI Components

The system includes a complete UI component library:

- `Button` - Multiple variants (primary, secondary, outline, ghost)
- `Card` - Content containers with gradients
- `Badge` - Status and category indicators
- `Progress` - Visual progress bars
- `Tabs` - Tab navigation
- `Skeleton` - Loading placeholders
- `EmptyState` - Empty content states
- `Tooltip` - Hover information
- `Collapsible` - Expandable sections
- `CopyButton` - One-click copy

## 🏗️ Database Schema

### Tables

- `users` - User accounts (extends Supabase auth)
- `user_profiles` - Resume and portfolio data
- `user_skills` - Normalized skill entries
- `job_requests` - Analysis requests
- `analysis_results` - Generated outputs
- `skill_taxonomy` - Canonical skill names

See `supabase/migrations/001_initial_schema.sql` for complete schema.

## 📊 Output Format

```typescript
interface FullAnalysisResponse {
  job_analysis: {
    job_title: string;
    company: string;
    core_skills: string[];
    tools: string[];
    experience_level: string;
    ats_keywords: string[];
  };
  skill_gap: {
    match_percentage: number;
    matching_skills: string[];
    missing_skills: Array<{
      skill: string;
      priority: 'high' | 'medium' | 'low';
      estimated_hours: number;
    }>;
  };
  roadmap: {
    total_weeks: number;
    weekly_plan: Array<{
      week: number;
      focus_skill: string;
      tasks: Array<{ title: string; hours: number }>;
      resources: Array<{ title: string; url: string }>;
    }>;
  };
  resume_suggestions: {
    improved_bullets: Array<{
      original: string;
      improved: string;
      keywords_added: string[];
    }>;
    ats_keywords: string[];
  };
  recommended_projects: {
    projects: Array<{
      name: string;
      description: string;
      tech_stack: string[];
      difficulty: string;
    }>;
  };
  github_tasks: {
    issues: Array<{
      title: string;
      body: string;
      labels: string[];
      checklist: string[];
    }>;
  };
  portfolio_updates: {
    skills_to_add: Array<{ name: string; category: string }>;
    bio_suggestion: string;
    headline_suggestion: string;
  };
}
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

🔗 **Live URL:** [https://skill-autofill.vercel.app/](https://skill-autofill.vercel.app/)

## 📝 License

MIT License - see [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

- Built with [Next.js](https://nextjs.org/)
- Styled with [Tailwind CSS](https://tailwindcss.com/)
- Database by [Supabase](https://supabase.com/)
- Icons from [Heroicons](https://heroicons.com/)

---

**Made with ❤️ for developers who want to level up their careers**
