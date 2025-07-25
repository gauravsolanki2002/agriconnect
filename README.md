# AgriConnect - Farmer's Digital Platform

AgriConnect is a comprehensive digital platform designed to empower farmers with modern technology solutions. It connects farmers with markets, provides real-time agricultural data, weather forecasts, and mandi rates.

## Features

- **Weather Forecast**: Get accurate weather predictions for farming activities
- **Mandi Rates**: Real-time market prices for agricultural commodities
- **Sell Produce**: Direct connection with buyers for better prices
- **Dashboard**: Analytics and management tools for farmers
- **User Authentication**: Secure login and registration system

## Tech Stack

- **Frontend**: React 18 + TypeScript
- **Styling**: Tailwind CSS
- **Icons**: Lucide React
- **Backend**: Supabase (Database + Authentication)
- **Build Tool**: Vite
- **Deployment**: Netlify

## Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Supabase account

### Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd agriconnect
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file in root directory:
```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

4. Set up Supabase database (see Database Setup section)

5. Start development server:
```bash
npm run dev
```

## Database Setup

Create these tables in your Supabase database:

```sql
-- Produce table
CREATE TABLE produce (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  user_id UUID REFERENCES auth.users(id),
  name TEXT NOT NULL,
  category TEXT NOT NULL,
  quantity DECIMAL NOT NULL,
  unit TEXT NOT NULL,
  price_per_unit DECIMAL NOT NULL,
  description TEXT,
  location TEXT NOT NULL,
  harvest_date DATE NOT NULL,
  expiry_date DATE,
  image_url TEXT,
  status TEXT DEFAULT 'available',
  created_at TIMESTAMP DEFAULT NOW()
);

-- Enable RLS
ALTER TABLE produce ENABLE ROW LEVEL SECURITY;

-- RLS Policies
CREATE POLICY "Users can view all produce" ON produce FOR SELECT USING (true);
CREATE POLICY "Users can insert their own produce" ON produce FOR INSERT WITH CHECK (auth.uid() = user_id);
CREATE POLICY "Users can update their own produce" ON produce FOR UPDATE USING (auth.uid() = user_id);
CREATE POLICY "Users can delete their own produce" ON produce FOR DELETE USING (auth.uid() = user_id);
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## Project Structure

```
src/
├── components/
│   └── Layout/
│       ├── Header.tsx
│       └── Footer.tsx
├── contexts/
│   └── AuthContext.tsx
├── lib/
│   └── supabase.ts
├── pages/
│   ├── Home.tsx
│   ├── Weather.tsx
│   ├── MandiRates.tsx
│   ├── SellProduce.tsx
│   ├── Dashboard.tsx
│   ├── Login.tsx
│   └── SignUp.tsx
├── types/
│   └── index.ts
├── App.tsx
├── main.tsx
└── index.css
```

## Environment Variables

Create a `.env` file with:

```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License.

## Contact

- Email: support@agriconnect.com
- Phone: +91 1234567890
- Address: India

## Acknowledgments

- Thanks to all farmers who inspired this project
- Supabase for providing excellent backend services
- React and Vite communities for amazing tools