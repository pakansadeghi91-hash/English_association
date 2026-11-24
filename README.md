# English_association
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>English Association</title>
  <link rel="stylesheet" href="styles.css">
  <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
  <script defer src="app.js"></script>
</head>
<body>

<header>
  <div class="logo">
    <span>EA</span>
    English Association
  </div>

  <nav>
    <a href="#home">خانه</a>
    <a href="#facts">دانستنی‌ها</a>
    <a href="#articles">مقالات</a>
    <a href="#quiz">کوییز</a>
    <a href="#community">انجمن</a>
    <a href="#contact">ارتباط با ما</a>
  </nav>

  <div id="authActions">
    <button onclick="openAuth('login')">ورود</button>
    <button onclick="openAuth('signup')">ثبت‌نام</button>
  </div>

  <div id="userActions" class="hidden">
    <span id="userEmail"></span>
    <button id="logoutBtn">خروج</button>
  </div>
</header>

<main>

<section id="home" class="hero">
  <div>
    <span>ENGLISH LEARNING COMMUNITY</span>
    <h1>زبان جدید،<br>فرصت‌های تازه.</h1>
    <p>
      به انجمن زبان انگلیسی خوش آمدید.
      جایی برای یادگیری، تمرین و پیشرفت در کنار یکدیگر.
    </p>
    <a href="#articles" class="primary">مطالعه مقالات</a>
    <a href="#quiz" class="secondary">شروع آزمون</a>
  </div>
  <div class="hero-logo">EA</div>
</section>

<section id="facts" class="section">
  <h2>دانستنی‌های زبان انگلیسی</h2>
  <div id="factsGrid" class="grid"></div>
</section>

<section id="articles" class="section">
  <h2>مقالات آموزشی</h2>
  <div id="articlesGrid" class="grid"></div>
</section>

<section id="quiz" class="section">
  <h2>کوییز زبان انگلیسی</h2>
  <div class="quiz-card" id="quizCard">
    <div id="quizContent"></div>
    <span id="quizProgress"></span>
  </div>
</section>

<section id="community" class="section community">
  <h2>به خانواده ما بپیوندید</h2>
  <p>با اعضای انجمن یاد بگیرید و تجربه‌هایتان را به اشتراک بگذارید.</p>
  <button onclick="openAuth('signup')">عضویت در انجمن</button>
</section>

<section id="contact" class="section">
  <h2>ارتباط با ما</h2>
  <form id="contactForm">
    <input name="name" placeholder="نام شما" required>
    <input name="email" type="email" placeholder="ایمیل" required>
    <textarea name="message" placeholder="پیام شما" required></textarea>
    <button type="submit">ارسال پیام</button>
    <p id="contactMessage"></p>
  </form>
</section>

</main>

<footer>
  <h3>English Association</h3>
  <p>Learn Together, Grow Together.</p>
  <p>© 2026 English Association</p>
</footer>

<div id="authModal" class="modal hidden">
  <div class="modal-content">
    <button onclick="closeAuth()">×</button>
    <h2 id="authTitle">ورود</h2>

    <form id="authForm">
      <label id="nameField" class="hidden">
        نام نمایشی
        <input name="displayName" placeholder="نام شما">
      </label>

      <input name="email" type="email" placeholder="ایمیل" required>
      <input name="password" type="password"
        placeholder="رمز عبور (حداقل ۸ کاراکتر)"
        minlength="8" required>

      <button type="submit" id="authSubmit">ورود</button>
      <p id="authMessage"></p>
    </form>

    <button id="switchAuth">ثبت‌نام</button>
  </div>
</div>

</body>
</html>
:root {
  --navy: #142b49;
  --gold: #d7ad63;
  --cream: #f8f6f0;
  --white: #ffffff;
  --text: #253448;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Tahoma, sans-serif;
  background: var(--white);
  color: var(--text);
  line-height: 1.9;
}

html {
  scroll-behavior: smooth;
}

header {
  background: white;
  padding: 18px 5%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 15px;
  box-shadow: 0 2px 15px #0000000a;
  position: sticky;
  top: 0;
  z-index: 10;
}

.logo {
  color: var(--navy);
  font-size: 20px;
  font-weight: bold;
}

.logo span {
  background: var(--navy);
  color: var(--gold);
  padding: 10px;
  border-radius: 10px;
  margin-left: 8px;
}

nav {
  display: flex;
  gap: 18px;
  flex-wrap: wrap;
}

nav a {
  color: var(--navy);
  text-decoration: none;
  font-size: 13px;
}

nav a:hover {
  color: var(--gold);
}

button, .primary, .secondary {
  border: none;
  border-radius: 8px;
  padding: 11px 20px;
  cursor: pointer;
  text-decoration: none;
  display: inline-block;
  font-size: 13px;
}

button, .primary {
  background: var(--navy);
  color: white;
}

.secondary {
  background: var(--cream);
  color: var(--navy);
  margin-right: 8px;
}

.hero {
  background: var(--cream);
  min-height: 480px;
  padding: 90px 8%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 30px;
}

.hero h1 {
  font-size: clamp(35px, 5vw, 60px);
  color: var(--navy);
  line-height: 1.5;
  margin: 15px 0;
}

.hero p {
  color: #68788b;
  max-width: 480px;
  margin-bottom: 25px;
}

.hero-logo {
  width: 250px;
  height: 250px;
  border-radius: 50%;
  background: var(--navy);
  color: var(--gold);
  display: grid;
  place-items: center;
  font-size: 75px;
  font-weight: bold;
  direction: ltr;
}

.section {
  padding: 75px 8%;
}

.section h2 {
  color: var(--navy);
  margin-bottom: 30px;
  font-size: 30px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.content-card {
  padding: 25px;
  border: 1px solid #e5e8ed;
  border-radius: 12px;
  background: white;
}

.content-card h3 {
  color: var(--navy);
  margin: 12px 0;
}

.content-card p {
  color: #718096;
  font-size: 13px;
}

.quiz-card {
  padding: 30px;
  border: 1px solid #e5e8ed;
  border-radius: 15px;
  max-width: 700px;
}

.answers {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  direction: ltr;
  margin: 20px 0;
}

.answer {
  background: var(--cream);
  color: var(--navy);
  border: 1px solid #ddd;
}

.answer:hover {
  background: #f1e6d2;
}

.community {
  background: var(--navy);
  color: white;
  text-align: center;
}

.community h2 {
  color: var(--gold);
}

#contactForm {
  max-width: 650px;
  display: grid;
  gap: 15px;
}

input, textarea {
  width: 100%;
  padding: 13px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font: inherit;
}

textarea {
  resize: vertical;
  min-height: 120px;
}

footer {
  background: #0e2035;
  color: white;
  text-align: center;
  padding: 35px;
}

.hidden {
  display: none !important;
}

.modal {
  position: fixed;
  inset: 0;
  background: #0009;
  display: grid;
  place-items: center;
  z-index: 20;
  padding: 20px;
}

.modal-content {
  background: white;
  width: 100%;
  max-width: 420px;
  padding: 30px;
  border-radius: 15px;
}

.modal-content form {
  display: grid;
  gap: 15px;
}

@media (max-width: 800px) {
  header {
    justify-content: center;
  }

  nav {
    justify-content: center;
  }

  .hero {
    flex-direction: column;
    text-align: center;
  }

  .hero-logo {
    width: 180px;
    height: 180px;
  }

  .grid {
    grid-template-columns: 1fr;
  }

  .answers {
    grid-template-columns: 1fr;
  }
}
const SUPABASE_URL = "YOUR_SUPABASE_PROJECT_URL";
const SUPABASE_ANON_KEY = "YOUR_SUPABASE_ANON_KEY";

const ready =
  SUPABASE_URL.startsWith("https://") &&
  !SUPABASE_URL.includes("YOUR_") &&
  !SUPABASE_ANON_KEY.includes("YOUR_");

const db = ready
  ? window.supabase.createClient(
      SUPABASE_URL,
      SUPABASE_ANON_KEY
    )
  : null;

const facts = [
  {
    title: "The English Alphabet",
    text: "الفبای انگلیسی ۲۶ حرف دارد."
  },
  {
    title: "English Vocabulary",
    text: "معنی بسیاری از واژه‌ها با توجه به متن تغییر می‌کند."
  },
  {
    title: "Global Language",
    text: "انگلیسی یکی از زبان‌های مهم ارتباط بین‌المللی است."
  }
];

const articles = [
  {
    title: "Learning Vocabulary",
    text: "برای یادگیری لغات جدید، آن‌ها را در جمله استفاده کنید."
  },
  {
    title: "English Grammar",
    text: "گرامر پایه به شما کمک می‌کند جملات دقیق‌تری بسازید."
  },
  {
    title: "Speaking Skills",
    text: "تمرین روزانه مکالمه به تقویت مهارت گفتاری کمک می‌کند."
  }
];

function escapeHTML(value) {
  return String(value).replace(/[&<>"']/g, char => ({
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&#39;"
  }[char]));
}

function renderCards(id, items) {
  document.getElementById(id).innerHTML =
    items.map(item => `
      <article class="content-card">
        <h3>${escapeHTML(item.title)}</h3>
        <p>${escapeHTML(item.text)}</p>
      </article>
    `).join("");
}

renderCards("factsGrid", facts);
renderCards("articlesGrid", articles);

const questions = [
  {
    q: "What is the plural of Child?",
    a: ["Childs", "Children", "Childes", "Childrens"],
    correct: 1
  },
  {
    q: "Choose the correct sentence.",
    a: [
      "She go to school.",
      "She going school.",
      "She goes to school.",
      "She gone school."
    ],
    correct: 2
  },
  {
    q: "Opposite of Early?",
    a: ["Late", "Fast", "Short", "Near"],
    correct: 0
  },
  {
    q: "I ___ a student.",
    a: ["is", "are", "am", "be"],
    correct: 2
  },
  {
    q: "Which is a noun?",
    a: ["Quickly", "Beautiful", "Happiness", "Run"],
    correct: 2
  }
];

let current = 0;
let score = 0;
let answered = false;

function drawQuiz() {
  const host = document.getElementById("quizContent");

  document.getElementById("quizProgress").textContent =
    `سؤال ${Math.min(current + 1, questions.length)} از ${questions.length}`;

  if (current >= questions.length) {
    host.innerHTML = `
      <h3>آزمون تمام شد!</h3>
      <p>امتیاز شما: ${score} از ${questions.length}</p>
      <button onclick="restartQuiz()">تلاش دوباره</button>
    `;
    return;
  }

  const q = questions[current];
  answered = false;

  host.innerHTML = `
    <h3 dir="ltr">${escapeHTML(q.q)}</h3>
    <div class="answers">
      ${q.a.map((answer, i) => `
        <button class="answer" data-index="${i}">
          ${String.fromCharCode(65+i)}. ${escapeHTML(answer)}
        </button>
      `).join("")}
    </div>
    <p id="quizFeedback"></p>
    <button id="nextBtn" disabled>سؤال بعدی</button>
  `;

  host.querySelectorAll("[data-index]").forEach(button => {
    button.onclick = () => {
      if (answered) return;
      answered = true;

      const chosen = Number(button.dataset.index);

      if (chosen === q.correct) score++;

      document.getElementById("quizFeedback").textContent =
        chosen === q.correct ? "آفرین! پاسخ درست است." : "پاسخ درست مشخص شد.";

      host.querySelectorAll("[data-index]").forEach((b, i) => {
        b.disabled = true;
        if (i === q.correct) b.style.borderColor = "green";
      });

      document.getElementById("nextBtn").disabled = false;
    };
  });

  document.getElementById("nextBtn").onclick = () => {
    current++;
    drawQuiz();
  };
}

function restartQuiz() {
  current = 0;
  score = 0;
  drawQuiz();
}

drawQuiz();

let authMode = "login";

function openAuth(mode) {
  authMode = mode;

  document.getElementById("authModal").classList.remove("hidden");
  document.getElementById("authTitle").textContent =
    mode === "login" ? "ورود به حساب" : "ثبت‌نام";

  document.getElementById("nameField").classList.toggle(
    "hidden",
    mode === "login"
  );

  document.getElementById("authSubmit").textContent =
    mode === "login" ? "ورود" : "ثبت‌نام";

  document.getElementById("authMessage").textContent = "";
}

function closeAuth() {
  document.getElementById("authModal").classList.add("hidden");
}

document.getElementById("switchAuth").onclick = () => {
  openAuth(authMode === "login" ? "signup" : "login");
};

document.getElementById("authForm").onsubmit = async event => {
  event.preventDefault();

  const form = new FormData(event.target);
  const email = form.get("email").trim();
  const password = form.get("password");
  const message = document.getElementById("authMessage");

  if (!db) {
    message.textContent = "ابتدا Supabase را تنظیم کن.";
    return;
  }

  try {
    if (authMode === "signup") {
      const { data, error } = await db.auth.signUp({
        email,
        password,
        options: {
          data: {
            display_name: form.get("displayName") || ""
          }
        }
      });

      if (error) throw error;

      message.textContent = data.session
        ? "ثبت‌نام انجام شد."
        : "ایمیل تأیید را بررسی کن.";
    } else {
      const { error } = await db.auth.signInWithPassword({
        email,
        password
      });

      if (error) throw error;

      closeAuth();
    }
  } catch (error) {
    message.textContent = error.message;
  }
};

async function refreshSession() {
  if (!db) return;

  const { data } = await db.auth.getSession();
  updateUser(data.session?.user);

  db.auth.onAuthStateChange((_event, session) => {
    updateUser(session?.user);
  });
}

function updateUser(user) {
  document.getElementById("authActions")
    .classList.toggle("hidden", !!user);

  document.getElementById("userActions")
    .classList.toggle("hidden", !user);

  document.getElementById("userEmail").textContent =
    user?.email || "";
}

document.getElementById("logoutBtn").onclick = async () => {
  if (db) await db.auth.signOut();
};

refreshSession();

document.getElementById("contactForm").onsubmit = async event => {
  event.preventDefault();

  if (!db) {
    document.getElementById("contactMessage").textContent =
      "ابتدا Supabase را تنظیم کن.";
    return;
  }

  const form = new FormData(event.target);

  const { error } = await db.from("contact_messages").insert({
    name: form.get("name"),
    email: form.get("email"),
    message: form.get("message")
  });

  document.getElementById("contactMessage").textContent =
    error ? "ارسال پیام ناموفق بود." : "پیام با موفقیت ثبت شد.";

  if (!error) event.target.reset();
};
create table if not exists public.profiles (
  id uuid primary key references auth.users(id) on delete cascade,
  display_name text default '',
  role text not null default 'member'
    check (role in ('member','admin')),
  created_at timestamptz default now()
);

create table if not exists public.articles (
  id bigint generated by default as identity primary key,
  title text not null,
  category text default 'General',
  excerpt text default '',
  body text default '',
  published boolean default false,
  created_at timestamptz default now()
);

create table if not exists public.quiz_results (
  id bigint generated by default as identity primary key,
  user_id uuid references auth.users(id) on delete cascade,
  score integer not null,
  total integer not null,
  created_at timestamptz default now()
);

create table if not exists public.contact_messages (
  id bigint generated by default as identity primary key,
  name text not null,
  email text not null,
  message text not null,
  created_at timestamptz default now()
);

alter table public.profiles enable row level security;
alter table public.articles enable row level security;
alter table public.quiz_results enable row level security;
alter table public.contact_messages enable row level security;

create or replace function public.handle_new_user()
returns trigger
language plpgsql
security definer
set search_path = ''
as $$
begin
  insert into public.profiles(id, display_name)
  values (
    new.id,
    coalesce(new.raw_user_meta_data ->> 'display_name','')
  );
  return new;
end;
$$;

drop trigger if exists on_auth_user_created on auth.users;

create trigger on_auth_user_created
after insert on auth.users
for each row execute procedure public.handle_new_user();

create policy "profile read own"
on public.profiles for select to authenticated
using (auth.uid() = id);

create policy "profile update own"
on public.profiles for update to authenticated
using (auth.uid() = id)
with check (auth.uid() = id and role = 'member');

create policy "published articles readable"
on public.articles for select
using (published = true);

create policy "admins manage articles"
on public.articles for all to authenticated
using (
  exists (
    select 1 from public.profiles p
    where p.id = auth.uid() and p.role = 'admin'
  )
)
with check (
  exists (
    select 1 from public.profiles p
    where p.id = auth.uid() and p.role = 'admin'
  )
);

create policy "read own quiz results"
on public.quiz_results for select to authenticated
using (auth.uid() = user_id);

create policy "insert own quiz results"
on public.quiz_results for insert to authenticated
with check (auth.uid() = user_id);

create policy "anyone can send contact message"
on public.contact_messages for insert to anon, authenticated
with check (
  char_length(name) between 1 and 80
  and char_length(email) between 5 and 160
  and char_length(message) between 1 and 2000
);
