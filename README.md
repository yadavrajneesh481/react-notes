# 🧠 React.js Complete Deep Notes + Interview Questions
*Comprehensive Course Summary with Detailed Hinglish Explanations & Multiple Examples*

## 📚 Course Outline Completed (40-60 Days)

### Week 1-2: Introduction and Fundamentals
- **Day 1-2:** Introduction to React
- **Day 3-4:** JavaScript ES6+ Review  
- **Day 5-6:** JSX and Components
- **Day 7-8:** Props and State
- **Day 9-10:** Handling Events

### Week 3-4: Intermediate Concepts
- **Day 11-12:** Lists and Keys
- **Day 13-14:** Forms in React
- **Day 15-16:** Component Lifecycle
- **Day 17-18:** Conditional Rendering
- **Day 19-20:** Styling in React

### Week 5-6: Advanced State Management
- **Day 21-22:** Context API
- **Day 23-25:** Redux
- **Day 26-27:** Redux Middleware
- **Day 28:** Reselect

### Week 7-8: Routing and Performance
- **Day 29-30:** React Router
- **Day 31-32:** Code Splitting
- **Day 33-34:** Performance Optimization

### Week 9-10: Testing and Advanced Patterns
- **Day 35-36:** Testing React Applications
- **Day 37-38:** Advanced Hooks
- **Day 39:** Higher-Order Components (HOCs)
- **Day 40:** Render Props

---

## 🗓 WEEK 1–2: Introduction and Fundamentals

### 🔹 Day 1-2: Introduction to React - DEEP DIVE

**Definition (English):**
React is a declarative, efficient, and flexible JavaScript library for building user interfaces. It's component-based, meaning you build encapsulated components that manage their own state, then compose them to make complex UIs. React uses a Virtual DOM for optimal performance and follows a unidirectional data flow pattern.

**Hinglish Deep Explanation:**
React ek powerful JavaScript library hai jo Facebook (Meta) ne banaya hai. Iska main purpose hai user interfaces banana jo fast, interactive aur maintainable ho. 

**Key Concepts:**
1. **Virtual DOM:** Real DOM expensive hai manipulate karne ke liye. React ek virtual copy banata hai memory mein, changes compare karta hai, aur sirf necessary parts ko update karta hai.
2. **Component-Based:** Har UI piece ek separate component hota hai - jaise LEGO blocks.
3. **Declarative:** Aap sirf batate hain ki UI kaisa dikhna chahiye, React figure out karta hai kaise achieve karna hai.
4. **Unidirectional Data Flow:** Data sirf ek direction mein flow hota hai - parent se child tak.

**Example 1: Basic React Component**
```jsx
// Simple functional component
function Welcome() {
  return <h1>Welcome to React World!</h1>;
}

// Using the component
function App() {
  return (
    <div>
      <Welcome />
      <p>This is my first React app</p>
    </div>
  );
}

export default App;
```

**Example 2: Component with Dynamic Content**
```jsx
function UserGreeting({ userName, timeOfDay }) {
  const greeting = timeOfDay === 'morning' ? 'Good Morning' : 'Good Evening';
  
  return (
    <div>
      <h2>{greeting}, {userName}!</h2>
      <p>Welcome back to your dashboard</p>
    </div>
  );
}

// Usage
function App() {
  return (
    <div>
      <UserGreeting userName="Rajesh" timeOfDay="morning" />
      <UserGreeting userName="Priya" timeOfDay="evening" />
    </div>
  );
}
```

**Example 3: React vs Vanilla JavaScript Comparison**
```javascript
// Vanilla JavaScript - Imperative
const button = document.createElement('button');
button.textContent = 'Click me';
button.addEventListener('click', function() {
  const counter = document.getElementById('counter');
  counter.textContent = parseInt(counter.textContent) + 1;
});
document.body.appendChild(button);

// React - Declarative
function Counter() {
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

**Why React is Popular:**
- **Reusability:** Components ko multiple jagah use kar sakte hain
- **Performance:** Virtual DOM se fast updates
- **Developer Experience:** Great debugging tools aur ecosystem
- **Community:** Huge community support aur libraries
- **Job Market:** High demand in industry

**Interview Questions:**
1. What is React and what problems does it solve?
2. Explain Virtual DOM and how it improves performance?
3. What is the difference between React and other frameworks like Angular or Vue?
4. What are the main features of React?
5. Why is React called a library and not a framework?

---### 🔹 Day 
3-4: JavaScript ES6+ Review - DEEP DIVE

**Definition (English):**
ES6 (ECMAScript 2015) and later versions introduced modern JavaScript features that are essential for React development. These features include arrow functions, destructuring, spread/rest operators, template literals, classes, modules, promises, and async/await.

**Hinglish Deep Explanation:**
React modern JavaScript features par heavily depend karta hai. Ye features code ko clean, readable aur efficient banate hain. Agar ye concepts clear nahi hain to React samajhna mushkil ho jata hai.

**1. Arrow Functions - Deep Understanding**

**Traditional vs Arrow Functions:**
```javascript
// Traditional function
function add(a, b) {
  return a + b;
}

// Arrow function - concise
const add = (a, b) => a + b;

// Arrow function - with body
const multiply = (a, b) => {
  const result = a * b;
  console.log(`Result: ${result}`);
  return result;
};

// Single parameter - no parentheses needed
const square = x => x * x;

// No parameters - empty parentheses required
const getRandomNumber = () => Math.random();
```

**Example 1: Arrow Functions in React Event Handlers**
```jsx
function ButtonComponent() {
  const handleClick = () => {
    console.log('Button clicked!');
  };

  // Inline arrow function
  return (
    <div>
      <button onClick={handleClick}>Click Me</button>
      <button onClick={() => alert('Inline function!')}>Alert</button>
    </div>
  );
}
```

**Example 2: Arrow Functions with Array Methods**
```jsx
function UserList({ users }) {
  // Using arrow functions with map
  const userItems = users.map(user => (
    <li key={user.id}>
      {user.name} - {user.email}
    </li>
  ));

  // Filtering with arrow functions
  const activeUsers = users.filter(user => user.isActive);

  return (
    <div>
      <h3>All Users:</h3>
      <ul>{userItems}</ul>
      <h3>Active Users: {activeUsers.length}</h3>
    </div>
  );
}
```

**2. Destructuring - Deep Understanding**

**Object Destructuring:**
```javascript
// Basic object destructuring
const user = { name: 'Raj', age: 25, city: 'Mumbai' };
const { name, age } = user;

// Renaming variables
const { name: userName, age: userAge } = user;

// Default values
const { name, age, country = 'India' } = user;

// Nested destructuring
const student = {
  info: { name: 'Priya', grade: 'A' },
  subjects: ['Math', 'Science']
};
const { info: { name, grade }, subjects } = student;
```

**Example 1: Props Destructuring in React**
```jsx
// Without destructuring
function UserCard(props) {
  return (
    <div>
      <h3>{props.user.name}</h3>
      <p>Age: {props.user.age}</p>
      <p>Email: {props.user.email}</p>
    </div>
  );
}

// With destructuring - cleaner
function UserCard({ user: { name, age, email }, isActive }) {
  return (
    <div className={isActive ? 'active' : 'inactive'}>
      <h3>{name}</h3>
      <p>Age: {age}</p>
      <p>Email: {email}</p>
    </div>
  );
}
```

**Array Destructuring:**
```javascript
// Basic array destructuring
const colors = ['red', 'green', 'blue'];
const [first, second, third] = colors;

// Skipping elements
const [primary, , tertiary] = colors;

// Rest operator with destructuring
const [head, ...tail] = colors;
console.log(head); // 'red'
console.log(tail); // ['green', 'blue']
```

**Example 2: useState Hook Destructuring**
```jsx
import { useState } from 'react';

function Counter() {
  // Array destructuring with useState
  const [count, setCount] = useState(0);
  const [name, setName] = useState('');
  const [user, setUser] = useState({ name: '', email: '' });

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      
      <input 
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Enter name"
      />
    </div>
  );
}
```

**3. Spread and Rest Operators - Deep Understanding**

**Spread Operator (...):**
```javascript
// Array spreading
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

// Object spreading
const user = { name: 'Raj', age: 25 };
const updatedUser = { ...user, city: 'Delhi' }; // { name: 'Raj', age: 25, city: 'Delhi' }

// Function arguments spreading
const numbers = [1, 2, 3, 4, 5];
const max = Math.max(...numbers);
```

**Example 1: Spread in React State Updates**
```jsx
function UserProfile() {
  const [user, setUser] = useState({
    name: 'Raj',
    email: 'raj@example.com',
    preferences: { theme: 'dark', language: 'en' }
  });

  const updateName = (newName) => {
    setUser({ ...user, name: newName });
  };

  const updatePreferences = (newTheme) => {
    setUser({
      ...user,
      preferences: { ...user.preferences, theme: newTheme }
    });
  };

  return (
    <div>
      <h3>{user.name}</h3>
      <button onClick={() => updateName('Rajesh')}>Update Name</button>
      <button onClick={() => updatePreferences('light')}>Light Theme</button>
    </div>
  );
}
```

**Rest Operator:**
```javascript
// Function parameters
function sum(first, second, ...others) {
  console.log(first, second); // First two arguments
  console.log(others); // Array of remaining arguments
  return first + second + others.reduce((a, b) => a + b, 0);
}

// Object destructuring with rest
const user = { name: 'Raj', age: 25, city: 'Mumbai', country: 'India' };
const { name, ...otherDetails } = user;
console.log(otherDetails); // { age: 25, city: 'Mumbai', country: 'India' }
```

**Example 2: Rest in React Component Props**
```jsx
function Button({ children, variant, ...otherProps }) {
  return (
    <button 
      className={`btn btn-${variant}`}
      {...otherProps}  // Spread remaining props
    >
      {children}
    </button>
  );
}

// Usage
<Button 
  variant="primary" 
  onClick={handleClick}
  disabled={isLoading}
  data-testid="submit-btn"
>
  Submit
</Button>
```

**4. Template Literals - Deep Understanding**

```javascript
// Basic template literals
const name = 'Raj';
const age = 25;
const message = `Hello, my name is ${name} and I am ${age} years old.`;

// Multi-line strings
const htmlTemplate = `
  <div>
    <h1>${name}</h1>
    <p>Age: ${age}</p>
  </div>
`;

// Expression evaluation
const price = 100;
const tax = 0.18;
const total = `Total: ₹${price + (price * tax)}`;
```

**Example 3: Template Literals in React**
```jsx
function ProductCard({ product, isOnSale }) {
  const discountedPrice = product.price * 0.8;
  
  return (
    <div className={`product-card ${isOnSale ? 'on-sale' : ''}`}>
      <h3>{product.name}</h3>
      <p className="price">
        {isOnSale 
          ? `₹${discountedPrice} (was ₹${product.price})` 
          : `₹${product.price}`
        }
      </p>
      <p className="description">
        {`${product.description.substring(0, 100)}...`}
      </p>
    </div>
  );
}
```

**5. Modules (Import/Export) - Deep Understanding**

**Named Exports:**
```javascript
// utils.js
export const formatCurrency = (amount) => `₹${amount.toLocaleString()}`;
export const formatDate = (date) => date.toLocaleDateString('en-IN');

export function validateEmail(email) {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}

// Multiple exports at once
const API_URL = 'https://api.example.com';
const MAX_RETRY_ATTEMPTS = 3;
export { API_URL, MAX_RETRY_ATTEMPTS };
```

**Default Exports:**
```javascript
// Button.jsx
function Button({ children, onClick, variant = 'primary' }) {
  return (
    <button className={`btn btn-${variant}`} onClick={onClick}>
      {children}
    </button>
  );
}

export default Button;
```

**Importing:**
```javascript
// App.jsx
import Button from './components/Button'; // Default import
import { formatCurrency, validateEmail } from './utils'; // Named imports
import * as utils from './utils'; // Import all as namespace

function App() {
  return (
    <div>
      <Button onClick={() => console.log('Clicked!')}>
        Click Me
      </Button>
      <p>{formatCurrency(1000)}</p>
      <p>{utils.formatDate(new Date())}</p>
    </div>
  );
}
```

**Interview Questions:**
1. What is the difference between arrow functions and regular functions?
2. How does destructuring help in React development?
3. When would you use the spread operator vs rest operator?
4. What are template literals and their advantages?
5. Explain the difference between named exports and default exports?
6. How do arrow functions handle the 'this' keyword differently?
7. What is the difference between let, const, and var?

---### 🔹 Day
 5-6: JSX and Components - DEEP DIVE

**Definition (English):**
JSX (JavaScript XML) is a syntax extension for JavaScript that allows you to write HTML-like code within JavaScript. It's not HTML, but gets transpiled to React.createElement() calls. Components are the building blocks of React applications - they are reusable, independent pieces of UI that can be composed together to build complex interfaces.

**Hinglish Deep Explanation:**
JSX React ka special syntax hai jo HTML aur JavaScript ko mix karne ki facility deta hai. Ye browser ko directly samajh nahi aata, Babel jaise tools ise normal JavaScript mein convert karte hain. Components React ka core concept hai - ye UI ke chhote pieces hain jo reuse ho sakte hain.

**JSX Deep Understanding:**

**1. JSX Transpilation Process:**
```jsx
// JSX Code (what we write)
const element = <h1 className="greeting">Hello, World!</h1>;

// Transpiled JavaScript (what browser gets)
const element = React.createElement(
  'h1',
  { className: 'greeting' },
  'Hello, World!'
);

// Complex JSX
const complexElement = (
  <div className="container">
    <h1>Title</h1>
    <p>Description</p>
  </div>
);

// Transpiled version
const complexElement = React.createElement(
  'div',
  { className: 'container' },
  React.createElement('h1', null, 'Title'),
  React.createElement('p', null, 'Description')
);
```

**2. JSX Rules and Syntax:**
```jsx
// Rule 1: Must return single parent element
function ValidComponent() {
  return (
    <div>  {/* Single parent wrapper */}
      <h1>Title</h1>
      <p>Content</p>
    </div>
  );
}

// Using React Fragment to avoid extra div
function FragmentExample() {
  return (
    <>  {/* React Fragment - no extra DOM node */}
      <h1>Title</h1>
      <p>Content</p>
    </>
  );
}

// Rule 2: JavaScript expressions in curly braces
function ExpressionExample() {
  const name = 'Raj';
  const age = 25;
  const isAdult = age >= 18;
  
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>Age: {age}</p>
      <p>Status: {isAdult ? 'Adult' : 'Minor'}</p>
      <p>Random: {Math.random()}</p>
      <p>Calculation: {10 + 20}</p>
    </div>
  );
}
```

**Example 1: Advanced JSX with Conditional Rendering**
```jsx
function UserDashboard({ user, notifications, isLoading }) {
  const hasNotifications = notifications && notifications.length > 0;
  
  return (
    <div className="dashboard">
      {/* Conditional rendering with ternary */}
      {isLoading ? (
        <div className="loading">Loading...</div>
      ) : (
        <div className="content">
          <header className="dashboard-header">
            <h1>Welcome, {user.name}!</h1>
            {/* Conditional rendering with && */}
            {hasNotifications && (
              <span className="notification-badge">
                {notifications.length} new notifications
              </span>
            )}
          </header>
          
          <main>
            {/* Conditional content */}
            {user.isPremium ? (
              <div className="premium-content">
                <h2>Premium Features</h2>
                <ul>
                  <li>Advanced Analytics</li>
                  <li>Priority Support</li>
                </ul>
              </div>
            ) : (
              <div className="upgrade-prompt">
                <h2>Upgrade to Premium</h2>
                <button>Upgrade Now</button>
              </div>
            )}
          </main>
        </div>
      )}
    </div>
  );
}
```

**Example 2: JSX with Dynamic Styling**
```jsx
function StatusCard({ status, message, priority }) {
  // Dynamic class names
  const cardClass = `status-card status-${status} priority-${priority}`;
  
  // Inline styles (object)
  const cardStyle = {
    backgroundColor: status === 'success' ? '#d4edda' : '#f8d7da',
    borderColor: status === 'success' ? '#c3e6cb' : '#f5c6cb',
    padding: '1rem',
    borderRadius: '4px',
    margin: '0.5rem 0'
  };
  
  return (
    <div 
      className={cardClass}
      style={cardStyle}
      data-status={status}  // Custom data attribute
    >
      <h3 style={{ color: status === 'success' ? '#155724' : '#721c24' }}>
        {status.toUpperCase()}
      </h3>
      <p>{message}</p>
      
      {/* Conditional icon based on status */}
      <span className="icon">
        {status === 'success' ? '✅' : status === 'error' ? '❌' : '⚠️'}
      </span>
    </div>
  );
}
```

**Components Deep Understanding:**

**1. Functional Components (Modern Approach):**
```jsx
// Basic functional component
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

// Arrow function component
const Greeting = (props) => {
  return <h1>Hello, {props.name}!</h1>;
};

// Implicit return (for simple components)
const Greeting = ({ name }) => <h1>Hello, {name}!</h1>;

// Component with multiple props
function UserCard({ name, email, avatar, isOnline, lastSeen }) {
  return (
    <div className="user-card">
      <img src={avatar} alt={`${name}'s avatar`} />
      <div className="user-info">
        <h3>{name}</h3>
        <p>{email}</p>
        <span className={`status ${isOnline ? 'online' : 'offline'}`}>
          {isOnline ? 'Online' : `Last seen: ${lastSeen}`}
        </span>
      </div>
    </div>
  );
}
```

**2. Class Components (Legacy but Important to Know):**
```jsx
import React, { Component } from 'react';

class UserCard extends Component {
  constructor(props) {
    super(props);
    this.state = {
      isExpanded: false,
      likeCount: 0
    };
  }
  
  handleToggle = () => {
    this.setState({ isExpanded: !this.state.isExpanded });
  }
  
  handleLike = () => {
    this.setState({ likeCount: this.state.likeCount + 1 });
  }
  
  render() {
    const { name, bio, avatar } = this.props;
    const { isExpanded, likeCount } = this.state;
    
    return (
      <div className="user-card">
        <img src={avatar} alt={name} />
        <h3>{name}</h3>
        
        {isExpanded && <p>{bio}</p>}
        
        <div className="actions">
          <button onClick={this.handleToggle}>
            {isExpanded ? 'Show Less' : 'Show More'}
          </button>
          <button onClick={this.handleLike}>
            Like ({likeCount})
          </button>
        </div>
      </div>
    );
  }
}
```

**Example 3: Component Composition**
```jsx
// Small, focused components
function Avatar({ src, alt, size = 'medium' }) {
  const sizeClass = `avatar avatar-${size}`;
  return <img className={sizeClass} src={src} alt={alt} />;
}

function UserName({ name, isVerified }) {
  return (
    <span className="username">
      {name}
      {isVerified && <span className="verified-badge">✓</span>}
    </span>
  );
}

function UserStats({ followers, following, posts }) {
  return (
    <div className="user-stats">
      <span>{posts} posts</span>
      <span>{followers} followers</span>
      <span>{following} following</span>
    </div>
  );
}

// Composed component using smaller components
function UserProfile({ user }) {
  return (
    <div className="user-profile">
      <div className="profile-header">
        <Avatar 
          src={user.avatar} 
          alt={user.name} 
          size="large" 
        />
        <div className="profile-info">
          <UserName 
            name={user.name} 
            isVerified={user.isVerified} 
          />
          <p className="bio">{user.bio}</p>
          <UserStats 
            followers={user.followers}
            following={user.following}
            posts={user.posts}
          />
        </div>
      </div>
    </div>
  );
}
```

**3. Component Best Practices:**
```jsx
// Good: Single Responsibility Principle
function SearchInput({ onSearch, placeholder }) {
  const [query, setQuery] = useState('');
  
  const handleSubmit = (e) => {
    e.preventDefault();
    onSearch(query);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder={placeholder}
      />
      <button type="submit">Search</button>
    </form>
  );
}

// Good: Prop validation with default values
function Button({ 
  children, 
  variant = 'primary', 
  size = 'medium', 
  disabled = false,
  onClick 
}) {
  const buttonClass = `btn btn-${variant} btn-${size}`;
  
  return (
    <button 
      className={buttonClass}
      disabled={disabled}
      onClick={onClick}
    >
      {children}
    </button>
  );
}

// Good: Conditional rendering patterns
function NotificationList({ notifications }) {
  if (!notifications || notifications.length === 0) {
    return (
      <div className="empty-state">
        <p>No notifications yet</p>
      </div>
    );
  }
  
  return (
    <div className="notification-list">
      {notifications.map(notification => (
        <NotificationItem 
          key={notification.id} 
          notification={notification} 
        />
      ))}
    </div>
  );
}
```

**JSX Gotchas and Common Mistakes:**
```jsx
// ❌ Wrong: Using 'class' instead of 'className'
function WrongExample() {
  return <div class="container">Content</div>; // Error!
}

// ✅ Correct: Use 'className'
function CorrectExample() {
  return <div className="container">Content</div>;
}

// ❌ Wrong: Self-closing tags not closed
function WrongSelfClosing() {
  return <input type="text">; // Error!
}

// ✅ Correct: Self-closing tags must be closed
function CorrectSelfClosing() {
  return <input type="text" />;
}

// ❌ Wrong: Multiple root elements
function WrongMultipleRoots() {
  return (
    <h1>Title</h1>
    <p>Content</p>  // Error!
  );
}

// ✅ Correct: Single root or Fragment
function CorrectSingleRoot() {
  return (
    <>
      <h1>Title</h1>
      <p>Content</p>
    </>
  );
}
```

**Interview Questions:**
1. What is JSX and how is it different from HTML?
2. How does JSX get converted to JavaScript?
3. What are the rules for writing JSX?
4. What is the difference between functional and class components?
5. Why do we use className instead of class in JSX?
6. What is React Fragment and when would you use it?
7. How do you handle conditional rendering in JSX?
8. What are the benefits of component composition?
9. Can you write React without JSX?
10. What are some common JSX gotchas or mistakes?

---##
# 🔹 Day 7-8: Props and State - DEEP DIVE

**Definition (English):**
Props (properties) are read-only data passed from parent components to child components, enabling component communication and reusability. State is mutable data that belongs to a component and can change over time, triggering re-renders when updated. Props flow down (unidirectional data flow) while state is managed locally within components.

**Hinglish Deep Explanation:**
Props ek tarah ka data hai jo parent component se child component tak jaata hai - ye read-only hota hai, matlab child component ise change nahi kar sakta. State component ka apna internal data hai jo time ke saath change ho sakta hai. Jab state change hoti hai, component re-render hota hai aur UI update ho jaata hai.

**Props Deep Understanding:**

**1. Basic Props Usage:**
```jsx
// Parent Component
function App() {
  const user = {
    name: 'Rajesh Kumar',
    age: 28,
    email: 'rajesh@example.com',
    isActive: true
  };
  
  return (
    <div>
      <UserProfile 
        user={user}
        showEmail={true}
        theme="dark"
        onUserClick={() => console.log('User clicked')}
      />
    </div>
  );
}

// Child Component receiving props
function UserProfile(props) {
  console.log(props); // { user: {...}, showEmail: true, theme: "dark", onUserClick: f }
  
  return (
    <div className={`profile profile-${props.theme}`}>
      <h2>{props.user.name}</h2>
      <p>Age: {props.user.age}</p>
      {props.showEmail && <p>Email: {props.user.email}</p>}
      <button onClick={props.onUserClick}>
        View Profile
      </button>
    </div>
  );
}
```

**2. Props Destructuring (Modern Approach):**
```jsx
// Destructuring in function parameters
function UserProfile({ user, showEmail, theme, onUserClick }) {
  return (
    <div className={`profile profile-${theme}`}>
      <h2>{user.name}</h2>
      <p>Age: {user.age}</p>
      {showEmail && <p>Email: {user.email}</p>}
      <button onClick={onUserClick}>View Profile</button>
    </div>
  );
}

// Nested destructuring
function UserProfile({ user: { name, age, email }, showEmail, theme }) {
  return (
    <div className={`profile profile-${theme}`}>
      <h2>{name}</h2>
      <p>Age: {age}</p>
      {showEmail && <p>Email: {email}</p>}
    </div>
  );
}

// Default values in destructuring
function Button({ 
  children, 
  variant = 'primary', 
  size = 'medium', 
  disabled = false,
  onClick = () => {} 
}) {
  return (
    <button 
      className={`btn btn-${variant} btn-${size}`}
      disabled={disabled}
      onClick={onClick}
    >
      {children}
    </button>
  );
}
```

**Example 1: Complex Props Passing**
```jsx
// Product data
const products = [
  { id: 1, name: 'Laptop', price: 50000, category: 'Electronics', inStock: true },
  { id: 2, name: 'Book', price: 500, category: 'Education', inStock: false },
  { id: 3, name: 'Phone', price: 25000, category: 'Electronics', inStock: true }
];

// Main App Component
function App() {
  const handleAddToCart = (productId) => {
    console.log(`Added product ${productId} to cart`);
  };

  const handleViewDetails = (product) => {
    console.log('Viewing details for:', product);
  };

  return (
    <div className="app">
      <h1>Product Catalog</h1>
      <ProductList 
        products={products}
        onAddToCart={handleAddToCart}
        onViewDetails={handleViewDetails}
        currency="₹"
        showStock={true}
      />
    </div>
  );
}

// Product List Component
function ProductList({ products, onAddToCart, onViewDetails, currency, showStock }) {
  return (
    <div className="product-list">
      {products.map(product => (
        <ProductCard
          key={product.id}
          product={product}
          onAddToCart={onAddToCart}
          onViewDetails={onViewDetails}
          currency={currency}
          showStock={showStock}
        />
      ))}
    </div>
  );
}

// Product Card Component
function ProductCard({ product, onAddToCart, onViewDetails, currency, showStock }) {
  const { id, name, price, category, inStock } = product;
  
  return (
    <div className={`product-card ${!inStock ? 'out-of-stock' : ''}`}>
      <h3>{name}</h3>
      <p className="category">{category}</p>
      <p className="price">{currency}{price.toLocaleString()}</p>
      
      {showStock && (
        <p className={`stock-status ${inStock ? 'in-stock' : 'out-of-stock'}`}>
          {inStock ? 'In Stock' : 'Out of Stock'}
        </p>
      )}
      
      <div className="actions">
        <button 
          onClick={() => onViewDetails(product)}
          className="btn-secondary"
        >
          View Details
        </button>
        <button 
          onClick={() => onAddToCart(id)}
          disabled={!inStock}
          className="btn-primary"
        >
          Add to Cart
        </button>
      </div>
    </div>
  );
}
```

**3. Props Validation and Default Props:**
```jsx
import PropTypes from 'prop-types';

function UserCard({ name, age, email, avatar, isActive, onEdit }) {
  return (
    <div className="user-card">
      <img src={avatar} alt={name} />
      <h3>{name}</h3>
      <p>Age: {age}</p>
      <p>Email: {email}</p>
      <span className={`status ${isActive ? 'active' : 'inactive'}`}>
        {isActive ? 'Active' : 'Inactive'}
      </span>
      <button onClick={onEdit}>Edit</button>
    </div>
  );
}

// Props validation
UserCard.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number.isRequired,
  email: PropTypes.string.isRequired,
  avatar: PropTypes.string,
  isActive: PropTypes.bool,
  onEdit: PropTypes.func.isRequired
};

// Default props
UserCard.defaultProps = {
  avatar: '/default-avatar.png',
  isActive: false
};
```

**State Deep Understanding:**

**1. useState Hook - Basic to Advanced:**
```jsx
import { useState } from 'react';

function Counter() {
  // Basic state
  const [count, setCount] = useState(0);
  
  // Multiple state variables
  const [name, setName] = useState('');
  const [isVisible, setIsVisible] = useState(true);
  
  // Object state
  const [user, setUser] = useState({
    name: '',
    email: '',
    age: 0
  });
  
  // Array state
  const [items, setItems] = useState([]);
  
  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);
  const reset = () => setCount(0);
  
  // Updating object state (important: create new object)
  const updateUser = (field, value) => {
    setUser(prevUser => ({
      ...prevUser,
      [field]: value
    }));
  };
  
  // Adding to array state
  const addItem = (newItem) => {
    setItems(prevItems => [...prevItems, newItem]);
  };
  
  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
      <button onClick={reset}>Reset</button>
      
      <div>
        <input 
          value={name}
          onChange={(e) => setName(e.target.value)}
          placeholder="Enter name"
        />
        <p>Hello, {name}!</p>
      </div>
    </div>
  );
}
```

**Example 2: Complex State Management**
```jsx
function ShoppingCart() {
  // Complex state object
  const [cart, setCart] = useState({
    items: [],
    total: 0,
    discount: 0,
    isLoading: false
  });
  
  const [user, setUser] = useState({
    name: '',
    email: '',
    address: {
      street: '',
      city: '',
      pincode: ''
    }
  });
  
  // Add item to cart
  const addToCart = (product) => {
    setCart(prevCart => {
      const existingItem = prevCart.items.find(item => item.id === product.id);
      
      if (existingItem) {
        // Update quantity if item exists
        const updatedItems = prevCart.items.map(item =>
          item.id === product.id 
            ? { ...item, quantity: item.quantity + 1 }
            : item
        );
        
        return {
          ...prevCart,
          items: updatedItems,
          total: calculateTotal(updatedItems)
        };
      } else {
        // Add new item
        const newItems = [...prevCart.items, { ...product, quantity: 1 }];
        return {
          ...prevCart,
          items: newItems,
          total: calculateTotal(newItems)
        };
      }
    });
  };
  
  // Remove item from cart
  const removeFromCart = (productId) => {
    setCart(prevCart => {
      const updatedItems = prevCart.items.filter(item => item.id !== productId);
      return {
        ...prevCart,
        items: updatedItems,
        total: calculateTotal(updatedItems)
      };
    });
  };
  
  // Update user address
  const updateAddress = (field, value) => {
    setUser(prevUser => ({
      ...prevUser,
      address: {
        ...prevUser.address,
        [field]: value
      }
    }));
  };
  
  const calculateTotal = (items) => {
    return items.reduce((sum, item) => sum + (item.price * item.quantity), 0);
  };
  
  return (
    <div className="shopping-cart">
      <h2>Shopping Cart ({cart.items.length} items)</h2>
      
      {cart.items.map(item => (
        <div key={item.id} className="cart-item">
          <span>{item.name}</span>
          <span>Qty: {item.quantity}</span>
          <span>₹{item.price * item.quantity}</span>
          <button onClick={() => removeFromCart(item.id)}>Remove</button>
        </div>
      ))}
      
      <div className="cart-total">
        <h3>Total: ₹{cart.total}</h3>
      </div>
      
      <div className="user-info">
        <h3>Delivery Address</h3>
        <input
          value={user.address.street}
          onChange={(e) => updateAddress('street', e.target.value)}
          placeholder="Street"
        />
        <input
          value={user.address.city}
          onChange={(e) => updateAddress('city', e.target.value)}
          placeholder="City"
        />
        <input
          value={user.address.pincode}
          onChange={(e) => updateAddress('pincode', e.target.value)}
          placeholder="Pincode"
        />
      </div>
    </div>
  );
}
```

**Example 3: State with Form Handling**
```jsx
function UserRegistrationForm() {
  const [formData, setFormData] = useState({
    firstName: '',
    lastName: '',
    email: '',
    password: '',
    confirmPassword: '',
    agreeToTerms: false
  });
  
  const [errors, setErrors] = useState({});
  const [isSubmitting, setIsSubmitting] = useState(false);
  
  // Generic input handler
  const handleInputChange = (e) => {
    const { name, value, type, checked } = e.target;
    setFormData(prev => ({
      ...prev,
      [name]: type === 'checkbox' ? checked : value
    }));
    
    // Clear error when user starts typing
    if (errors[name]) {
      setErrors(prev => ({
        ...prev,
        [name]: ''
      }));
    }
  };
  
  // Validation function
  const validateForm = () => {
    const newErrors = {};
    
    if (!formData.firstName.trim()) {
      newErrors.firstName = 'First name is required';
    }
    
    if (!formData.email.trim()) {
      newErrors.email = 'Email is required';
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = 'Email is invalid';
    }
    
    if (formData.password.length < 6) {
      newErrors.password = 'Password must be at least 6 characters';
    }
    
    if (formData.password !== formData.confirmPassword) {
      newErrors.confirmPassword = 'Passwords do not match';
    }
    
    if (!formData.agreeToTerms) {
      newErrors.agreeToTerms = 'You must agree to terms';
    }
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };
  
  const handleSubmit = async (e) => {
    e.preventDefault();
    
    if (!validateForm()) return;
    
    setIsSubmitting(true);
    
    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 2000));
      console.log('Form submitted:', formData);
      alert('Registration successful!');
      
      // Reset form
      setFormData({
        firstName: '',
        lastName: '',
        email: '',
        password: '',
        confirmPassword: '',
        agreeToTerms: false
      });
    } catch (error) {
      console.error('Submission error:', error);
    } finally {
      setIsSubmitting(false);
    }
  };
  
  return (
    <form onSubmit={handleSubmit} className="registration-form">
      <h2>User Registration</h2>
      
      <div className="form-group">
        <input
          type="text"
          name="firstName"
          value={formData.firstName}
          onChange={handleInputChange}
          placeholder="First Name"
          className={errors.firstName ? 'error' : ''}
        />
        {errors.firstName && <span className="error-message">{errors.firstName}</span>}
      </div>
      
      <div className="form-group">
        <input
          type="email"
          name="email"
          value={formData.email}
          onChange={handleInputChange}
          placeholder="Email"
          className={errors.email ? 'error' : ''}
        />
        {errors.email && <span className="error-message">{errors.email}</span>}
      </div>
      
      <div className="form-group">
        <input
          type="password"
          name="password"
          value={formData.password}
          onChange={handleInputChange}
          placeholder="Password"
          className={errors.password ? 'error' : ''}
        />
        {errors.password && <span className="error-message">{errors.password}</span>}
      </div>
      
      <div className="form-group">
        <input
          type="password"
          name="confirmPassword"
          value={formData.confirmPassword}
          onChange={handleInputChange}
          placeholder="Confirm Password"
          className={errors.confirmPassword ? 'error' : ''}
        />
        {errors.confirmPassword && <span className="error-message">{errors.confirmPassword}</span>}
      </div>
      
      <div className="form-group">
        <label>
          <input
            type="checkbox"
            name="agreeToTerms"
            checked={formData.agreeToTerms}
            onChange={handleInputChange}
          />
          I agree to the terms and conditions
        </label>
        {errors.agreeToTerms && <span className="error-message">{errors.agreeToTerms}</span>}
      </div>
      
      <button 
        type="submit" 
        disabled={isSubmitting}
        className="submit-button"
      >
        {isSubmitting ? 'Registering...' : 'Register'}
      </button>
    </form>
  );
}
```

**State Update Patterns:**
```jsx
// ❌ Wrong: Direct mutation
const [user, setUser] = useState({ name: 'Raj', age: 25 });
user.age = 26; // Don't do this!
setUser(user); // Won't trigger re-render

// ✅ Correct: Create new object
setUser({ ...user, age: 26 });

// ❌ Wrong: Mutating array
const [items, setItems] = useState([1, 2, 3]);
items.push(4); // Don't do this!
setItems(items);

// ✅ Correct: Create new array
setItems([...items, 4]);

// Functional updates for complex state
setUser(prevUser => ({
  ...prevUser,
  preferences: {
    ...prevUser.preferences,
    theme: 'dark'
  }
}));
```

**Interview Questions:**
1. What is the difference between props and state?
2. Are props mutable or immutable?
3. How do you pass data from child to parent component?
4. What happens when you directly mutate state?
5. How do you update object and array state correctly?
6. What is prop drilling and how can you avoid it?
7. Can you modify props inside a component?
8. What are default props and how do you set them?
9. How do you validate props in React?
10. What is the difference between controlled and uncontrolled components?

---### 🔹 Day 9-
10: Handling Events - DEEP DIVE

**Definition (English):**
Event handling in React involves responding to user interactions like clicks, form submissions, keyboard input, mouse movements, etc. React uses SyntheticEvents, which are wrappers around native DOM events that provide consistent behavior across different browsers. Events in React follow the same patterns as regular DOM events but with some React-specific enhancements.

**Hinglish Deep Explanation:**
React mein events handle karna matlab user ke actions (jaise click, typing, hover) ko respond karna. React apne SyntheticEvents use karta hai jo native browser events ko wrap karte hain aur sabhi browsers mein same behavior dete hain. React events camelCase mein likhte hain (onClick, onChange) aur function reference pass karte hain.

**Event Handling Deep Understanding:**

**1. Basic Event Handling:**
```jsx
function EventBasics() {
  // Simple click handler
  const handleClick = () => {
    console.log('Button clicked!');
  };
  
  // Event object access
  const handleClickWithEvent = (event) => {
    console.log('Event type:', event.type);
    console.log('Target element:', event.target);
    console.log('Current target:', event.currentTarget);
  };
  
  // Inline event handlers
  return (
    <div>
      {/* Function reference */}
      <button onClick={handleClick}>
        Click Me
      </button>
      
      {/* Inline arrow function */}
      <button onClick={() => alert('Inline handler!')}>
        Alert Button
      </button>
      
      {/* Event object access */}
      <button onClick={handleClickWithEvent}>
        Event Info
      </button>
      
      {/* Multiple event types */}
      <div
        onClick={() => console.log('Div clicked')}
        onMouseEnter={() => console.log('Mouse entered')}
        onMouseLeave={() => console.log('Mouse left')}
        style={{ padding: '20px', border: '1px solid #ccc' }}
      >
        Hover over me!
      </div>
    </div>
  );
}
```

**2. Form Event Handling:**
```jsx
function FormEvents() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: '',
    category: 'general',
    subscribe: false
  });
  
  // Generic input change handler
  const handleInputChange = (event) => {
    const { name, value, type, checked } = event.target;
    
    setFormData(prevData => ({
      ...prevData,
      [name]: type === 'checkbox' ? checked : value
    }));
  };
  
  // Form submission handler
  const handleSubmit = (event) => {
    event.preventDefault(); // Prevent default form submission
    console.log('Form submitted:', formData);
    
    // Validation
    if (!formData.name.trim()) {
      alert('Name is required!');
      return;
    }
    
    // Process form data
    console.log('Processing form...');
  };
  
  // Focus and blur handlers
  const handleFocus = (event) => {
    event.target.style.borderColor = '#007bff';
  };
  
  const handleBlur = (event) => {
    event.target.style.borderColor = '#ccc';
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <div>
        <input
          type="text"
          name="name"
          value={formData.name}
          onChange={handleInputChange}
          onFocus={handleFocus}
          onBlur={handleBlur}
          placeholder="Your Name"
        />
      </div>
      
      <div>
        <input
          type="email"
          name="email"
          value={formData.email}
          onChange={handleInputChange}
          placeholder="Your Email"
        />
      </div>
      
      <div>
        <textarea
          name="message"
          value={formData.message}
          onChange={handleInputChange}
          placeholder="Your Message"
          rows="4"
        />
      </div>
      
      <div>
        <select name="category" value={formData.category} onChange={handleInputChange}>
          <option value="general">General</option>
          <option value="support">Support</option>
          <option value="feedback">Feedback</option>
        </select>
      </div>
      
      <div>
        <label>
          <input
            type="checkbox"
            name="subscribe"
            checked={formData.subscribe}
            onChange={handleInputChange}
          />
          Subscribe to newsletter
        </label>
      </div>
      
      <button type="submit">Submit</button>
    </form>
  );
}
```

**Example 1: Advanced Event Handling with State Management**
```jsx
function InteractiveCounter() {
  const [count, setCount] = useState(0);
  const [step, setStep] = useState(1);
  const [history, setHistory] = useState([]);
  const [isAutoIncrement, setIsAutoIncrement] = useState(false);
  
  // Button click handlers with parameters
  const handleIncrement = (customStep = step) => {
    const newCount = count + customStep;
    setCount(newCount);
    addToHistory(`Incremented by ${customStep} to ${newCount}`);
  };
  
  const handleDecrement = (customStep = step) => {
    const newCount = count - customStep;
    setCount(newCount);
    addToHistory(`Decremented by ${customStep} to ${newCount}`);
  };
  
  const handleReset = () => {
    setCount(0);
    addToHistory('Reset to 0');
  };
  
  const addToHistory = (action) => {
    const timestamp = new Date().toLocaleTimeString();
    setHistory(prev => [...prev, `${timestamp}: ${action}`]);
  };
  
  // Keyboard event handling
  const handleKeyPress = (event) => {
    switch(event.key) {
      case 'ArrowUp':
        event.preventDefault();
        handleIncrement();
        break;
      case 'ArrowDown':
        event.preventDefault();
        handleDecrement();
        break;
      case 'r':
      case 'R':
        if (event.ctrlKey) {
          event.preventDefault();
          handleReset();
        }
        break;
      default:
        break;
    }
  };
  
  // Double click handler
  const handleDoubleClick = () => {
    handleIncrement(10);
  };
  
  // Context menu handler (right click)
  const handleContextMenu = (event) => {
    event.preventDefault();
    const action = window.confirm('Reset counter?');
    if (action) {
      handleReset();
    }
  };
  
  return (
    <div 
      className="interactive-counter"
      onKeyDown={handleKeyPress}
      tabIndex="0" // Make div focusable for keyboard events
      style={{ padding: '20px', border: '2px solid #ccc', outline: 'none' }}
    >
      <h2>Interactive Counter</h2>
      <p>Use arrow keys, double-click, or right-click!</p>
      
      <div 
        className="counter-display"
        onDoubleClick={handleDoubleClick}
        onContextMenu={handleContextMenu}
        style={{ 
          fontSize: '2rem', 
          padding: '20px', 
          backgroundColor: '#f0f0f0',
          cursor: 'pointer'
        }}
      >
        Count: {count}
      </div>
      
      <div className="controls">
        <input
          type="number"
          value={step}
          onChange={(e) => setStep(parseInt(e.target.value) || 1)}
          min="1"
          style={{ width: '60px', marginRight: '10px' }}
        />
        
        <button onClick={() => handleIncrement()}>
          + {step}
        </button>
        
        <button onClick={() => handleDecrement()}>
          - {step}
        </button>
        
        <button onClick={() => handleIncrement(5)}>
          +5
        </button>
        
        <button onClick={() => handleIncrement(10)}>
          +10
        </button>
        
        <button onClick={handleReset}>
          Reset
        </button>
      </div>
      
      <div className="history">
        <h3>History:</h3>
        <ul style={{ maxHeight: '150px', overflowY: 'auto' }}>
          {history.slice(-10).map((entry, index) => (
            <li key={index}>{entry}</li>
          ))}
        </ul>
      </div>
    </div>
  );
}
```

**Example 2: Mouse and Touch Events**
```jsx
function MouseTracker() {
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });
  const [isMouseDown, setIsMouseDown] = useState(false);
  const [clickCount, setClickCount] = useState(0);
  const [dragStart, setDragStart] = useState(null);
  const [isDragging, setIsDragging] = useState(false);
  
  // Mouse move handler
  const handleMouseMove = (event) => {
    setMousePosition({
      x: event.clientX,
      y: event.clientY
    });
  };
  
  // Mouse down/up handlers
  const handleMouseDown = (event) => {
    setIsMouseDown(true);
    setDragStart({ x: event.clientX, y: event.clientY });
    setIsDragging(false);
  };
  
  const handleMouseUp = () => {
    setIsMouseDown(false);
    setDragStart(null);
    setIsDragging(false);
  };
  
  // Click handler with click counting
  const handleClick = () => {
    setClickCount(prev => prev + 1);
  };
  
  // Drag detection
  const handleMouseMoveWithDrag = (event) => {
    handleMouseMove(event);
    
    if (isMouseDown && dragStart) {
      const deltaX = Math.abs(event.clientX - dragStart.x);
      const deltaY = Math.abs(event.clientY - dragStart.y);
      
      if (deltaX > 5 || deltaY > 5) {
        setIsDragging(true);
      }
    }
  };
  
  // Touch events for mobile
  const handleTouchStart = (event) => {
    const touch = event.touches[0];
    setMousePosition({ x: touch.clientX, y: touch.clientY });
  };
  
  const handleTouchMove = (event) => {
    event.preventDefault(); // Prevent scrolling
    const touch = event.touches[0];
    setMousePosition({ x: touch.clientX, y: touch.clientY });
  };
  
  return (
    <div
      className="mouse-tracker"
      onMouseMove={handleMouseMoveWithDrag}
      onMouseDown={handleMouseDown}
      onMouseUp={handleMouseUp}
      onClick={handleClick}
      onTouchStart={handleTouchStart}
      onTouchMove={handleTouchMove}
      style={{
        height: '400px',
        border: '2px solid #333',
        position: 'relative',
        backgroundColor: isDragging ? '#ffe6e6' : '#f9f9f9',
        cursor: isDragging ? 'grabbing' : 'crosshair'
      }}
    >
      <div className="info" style={{ padding: '10px' }}>
        <p>Mouse Position: ({mousePosition.x}, {mousePosition.y})</p>
        <p>Mouse Down: {isMouseDown ? 'Yes' : 'No'}</p>
        <p>Dragging: {isDragging ? 'Yes' : 'No'}</p>
        <p>Click Count: {clickCount}</p>
      </div>
      
      {/* Cursor follower */}
      <div
        style={{
          position: 'absolute',
          left: mousePosition.x - 10,
          top: mousePosition.y - 10,
          width: '20px',
          height: '20px',
          backgroundColor: 'red',
          borderRadius: '50%',
          pointerEvents: 'none',
          transform: 'translate(-50%, -50%)'
        }}
      />
    </div>
  );
}
```

**Example 3: Keyboard Events and Input Handling**
```jsx
function KeyboardEventHandler() {
  const [inputValue, setInputValue] = useState('');
  const [keyHistory, setKeyHistory] = useState([]);
  const [shortcuts, setShortcuts] = useState([]);
  const [isShiftPressed, setIsShiftPressed] = useState(false);
  const [isCtrlPressed, setIsCtrlPressed] = useState(false);
  
  // Key down handler
  const handleKeyDown = (event) => {
    const { key, code, ctrlKey, shiftKey, altKey } = event;
    
    // Track modifier keys
    setIsShiftPressed(shiftKey);
    setIsCtrlPressed(ctrlKey);
    
    // Add to key history
    const keyInfo = {
      key,
      code,
      timestamp: Date.now(),
      modifiers: { ctrl: ctrlKey, shift: shiftKey, alt: altKey }
    };
    
    setKeyHistory(prev => [...prev.slice(-9), keyInfo]);
    
    // Handle shortcuts
    if (ctrlKey) {
      switch(key.toLowerCase()) {
        case 's':
          event.preventDefault();
          handleSave();
          break;
        case 'z':
          event.preventDefault();
          handleUndo();
          break;
        case 'y':
          event.preventDefault();
          handleRedo();
          break;
        default:
          break;
      }
    }
    
    // Handle special keys
    switch(key) {
      case 'Enter':
        if (shiftKey) {
          // Shift+Enter for new line (handled by textarea)
        } else {
          event.preventDefault();
          handleSubmit();
        }
        break;
      case 'Escape':
        handleClear();
        break;
      case 'Tab':
        // Let default behavior happen, but log it
        console.log('Tab pressed');
        break;
      default:
        break;
    }
  };
  
  // Key up handler
  const handleKeyUp = (event) => {
    if (event.key === 'Shift') setIsShiftPressed(false);
    if (event.key === 'Control') setIsCtrlPressed(false);
  };
  
  // Input change with validation
  const handleInputChange = (event) => {
    const value = event.target.value;
    setInputValue(value);
    
    // Real-time validation
    if (value.length > 100) {
      event.target.style.borderColor = 'red';
    } else {
      event.target.style.borderColor = '#ccc';
    }
  };
  
  // Paste handler
  const handlePaste = (event) => {
    const pastedText = event.clipboardData.getData('text');
    console.log('Pasted text:', pastedText);
    
    // Custom paste handling
    if (pastedText.includes('http')) {
      event.preventDefault();
      const cleanText = pastedText.replace(/https?:\/\/[^\s]+/g, '[LINK]');
      setInputValue(prev => prev + cleanText);
    }
  };
  
  // Action handlers
  const handleSave = () => {
    setShortcuts(prev => [...prev, 'Ctrl+S: Save']);
    console.log('Saved!');
  };
  
  const handleUndo = () => {
    setShortcuts(prev => [...prev, 'Ctrl+Z: Undo']);
    console.log('Undo!');
  };
  
  const handleRedo = () => {
    setShortcuts(prev => [...prev, 'Ctrl+Y: Redo']);
    console.log('Redo!');
  };
  
  const handleSubmit = () => {
    console.log('Submitted:', inputValue);
    setInputValue('');
  };
  
  const handleClear = () => {
    setInputValue('');
    setKeyHistory([]);
    setShortcuts([]);
  };
  
  return (
    <div className="keyboard-handler" style={{ padding: '20px' }}>
      <h2>Keyboard Event Handler</h2>
      <p>Try typing, using shortcuts (Ctrl+S, Ctrl+Z, Ctrl+Y), Enter, Escape</p>
      
      <div className="input-section">
        <textarea
          value={inputValue}
          onChange={handleInputChange}
          onKeyDown={handleKeyDown}
          onKeyUp={handleKeyUp}
          onPaste={handlePaste}
          placeholder="Type here... (Ctrl+S to save, Enter to submit, Escape to clear)"
          rows="4"
          cols="50"
          style={{ width: '100%', padding: '10px' }}
        />
        
        <div className="character-count">
          Characters: {inputValue.length}/100
          {inputValue.length > 100 && (
            <span style={{ color: 'red' }}> (Too long!)</span>
          )}
        </div>
      </div>
      
      <div className="status">
        <p>Shift: {isShiftPressed ? '✓' : '✗'}</p>
        <p>Ctrl: {isCtrlPressed ? '✓' : '✗'}</p>
      </div>
      
      <div className="key-history">
        <h3>Recent Keys:</h3>
        <ul>
          {keyHistory.map((keyInfo, index) => (
            <li key={index}>
              {keyInfo.key} 
              {keyInfo.modifiers.ctrl && ' + Ctrl'}
              {keyInfo.modifiers.shift && ' + Shift'}
              {keyInfo.modifiers.alt && ' + Alt'}
            </li>
          ))}
        </ul>
      </div>
      
      <div className="shortcuts-used">
        <h3>Shortcuts Used:</h3>
        <ul>
          {shortcuts.map((shortcut, index) => (
            <li key={index}>{shortcut}</li>
          ))}
        </ul>
      </div>
    </div>
  );
}
```

**Event Delegation and Bubbling:**
```jsx
function EventBubbling() {
  const handleParentClick = (event) => {
    console.log('Parent clicked');
    console.log('Event target:', event.target.tagName);
    console.log('Current target:', event.currentTarget.tagName);
  };
  
  const handleChildClick = (event) => {
    console.log('Child clicked');
    // event.stopPropagation(); // Uncomment to stop bubbling
  };
  
  const handleButtonClick = (event) => {
    console.log('Button clicked');
    event.stopPropagation(); // Stop event from bubbling to parent
  };
  
  return (
    <div 
      onClick={handleParentClick}
      style={{ padding: '20px', border: '2px solid blue' }}
    >
      <h3>Parent Div (Blue Border)</h3>
      
      <div 
        onClick={handleChildClick}
        style={{ padding: '20px', border: '2px solid red', margin: '10px' }}
      >
        <h4>Child Div (Red Border)</h4>
        
        <button onClick={handleButtonClick}>
          Button (Stops Propagation)
        </button>
        
        <button onClick={(e) => console.log('Button 2 clicked')}>
          Button 2 (Bubbles)
        </button>
      </div>
    </div>
  );
}
```

**Common Event Patterns:**
```jsx
// Debounced input
function DebouncedInput() {
  const [value, setValue] = useState('');
  const [debouncedValue, setDebouncedValue] = useState('');
  
  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, 500);
    
    return () => clearTimeout(timer);
  }, [value]);
  
  return (
    <div>
      <input
        value={value}
        onChange={(e) => setValue(e.target.value)}
        placeholder="Type to search..."
      />
      <p>Debounced value: {debouncedValue}</p>
    </div>
  );
}

// Throttled scroll
function ThrottledScroll() {
  const [scrollY, setScrollY] = useState(0);
  const [isThrottled, setIsThrottled] = useState(false);
  
  const handleScroll = () => {
    if (!isThrottled) {
      setScrollY(window.scrollY);
      setIsThrottled(true);
      
      setTimeout(() => {
        setIsThrottled(false);
      }, 100);
    }
  };
  
  useEffect(() => {
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, [isThrottled]);
  
  return (
    <div style={{ height: '200vh' }}>
      <div style={{ position: 'fixed', top: 0, left: 0 }}>
        Scroll Y: {scrollY}
      </div>
    </div>
  );
}
```

**Interview Questions:**
1. What are SyntheticEvents in React?
2. How do you prevent default behavior in React events?
3. What is event bubbling and how do you stop it?
4. How do you pass parameters to event handlers?
5. What's the difference between onClick and onclick?
6. How do you handle keyboard events in React?
7. What is event delegation and how does it work in React?
8. How do you handle form events in React?
9. What are the performance considerations with event handlers?
10. How do you handle touch events for mobile devices?

---## 🧩 W
EEK 3–4: Intermediate React Concepts

### 🔹 Day 11–12: Lists and Keys - DEEP DIVE

**Definition (English):**
Lists in React are used to render multiple similar elements dynamically from arrays of data. Keys are unique identifiers that help React identify which items have changed, been added, or removed, enabling efficient updates to the DOM. Keys should be stable, predictable, and unique among siblings.

**Hinglish Deep Explanation:**
React mein jab hume multiple similar elements render karne hote hain (jaise todo items, user cards, product list), tab hum arrays ka use karte hain. Keys React ko batate hain ki kaunsa element kya hai - ye performance ke liye bahut important hai. Agar keys nahi denge ya galat denge to React confused ho jaata hai aur unnecessary re-renders hote hain.

**Lists and Keys Deep Understanding:**

**1. Basic List Rendering:**
```jsx
function BasicList() {
  const fruits = ['Apple', 'Banana', 'Orange', 'Mango'];
  const numbers = [1, 2, 3, 4, 5];
  
  return (
    <div>
      {/* Simple string array */}
      <h3>Fruits:</h3>
      <ul>
        {fruits.map((fruit, index) => (
          <li key={index}>{fruit}</li>
        ))}
      </ul>
      
      {/* Number array with transformation */}
      <h3>Squared Numbers:</h3>
      <ul>
        {numbers.map((num, index) => (
          <li key={index}>
            {num} squared is {num * num}
          </li>
        ))}
      </ul>
      
      {/* Conditional rendering in lists */}
      <h3>Even Numbers Only:</h3>
      <ul>
        {numbers
          .filter(num => num % 2 === 0)
          .map((num, index) => (
            <li key={index}>{num}</li>
          ))
        }
      </ul>
    </div>
  );
}
```

**2. Object Arrays with Proper Keys:**
```jsx
function UserList() {
  const users = [
    { id: 1, name: 'Rajesh Kumar', email: 'rajesh@example.com', age: 28, isActive: true },
    { id: 2, name: 'Priya Sharma', email: 'priya@example.com', age: 25, isActive: false },
    { id: 3, name: 'Amit Singh', email: 'amit@example.com', age: 32, isActive: true },
    { id: 4, name: 'Sneha Patel', email: 'sneha@example.com', age: 29, isActive: true }
  ];
  
  return (
    <div className="user-list">
      <h2>User Directory</h2>
      
      {/* Using unique ID as key (BEST PRACTICE) */}
      {users.map(user => (
        <div key={user.id} className={`user-card ${user.isActive ? 'active' : 'inactive'}`}>
          <h3>{user.name}</h3>
          <p>Email: {user.email}</p>
          <p>Age: {user.age}</p>
          <span className="status">
            {user.isActive ? '🟢 Active' : '🔴 Inactive'}
          </span>
        </div>
      ))}
      
      {/* Filtered and sorted list */}
      <h3>Active Users (Sorted by Age):</h3>
      {users
        .filter(user => user.isActive)
        .sort((a, b) => a.age - b.age)
        .map(user => (
          <div key={user.id} className="user-summary">
            {user.name} ({user.age} years)
          </div>
        ))
      }
    </div>
  );
}
```

**Example 1: Dynamic List with CRUD Operations**
```jsx
function TodoList() {
  const [todos, setTodos] = useState([
    { id: 1, text: 'Learn React', completed: false, priority: 'high', createdAt: new Date('2024-01-01') },
    { id: 2, text: 'Build a project', completed: false, priority: 'medium', createdAt: new Date('2024-01-02') },
    { id: 3, text: 'Deploy to production', completed: true, priority: 'low', createdAt: new Date('2024-01-03') }
  ]);
  
  const [newTodo, setNewTodo] = useState('');
  const [filter, setFilter] = useState('all'); // all, active, completed
  const [sortBy, setSortBy] = useState('createdAt'); // createdAt, priority, text
  
  // Add new todo
  const addTodo = () => {
    if (newTodo.trim()) {
      const todo = {
        id: Date.now(), // Simple ID generation
        text: newTodo.trim(),
        completed: false,
        priority: 'medium',
        createdAt: new Date()
      };
      setTodos(prevTodos => [...prevTodos, todo]);
      setNewTodo('');
    }
  };
  
  // Toggle todo completion
  const toggleTodo = (id) => {
    setTodos(prevTodos =>
      prevTodos.map(todo =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      )
    );
  };
  
  // Delete todo
  const deleteTodo = (id) => {
    setTodos(prevTodos => prevTodos.filter(todo => todo.id !== id));
  };
  
  // Update todo text
  const updateTodo = (id, newText) => {
    setTodos(prevTodos =>
      prevTodos.map(todo =>
        todo.id === id ? { ...todo, text: newText } : todo
      )
    );
  };
  
  // Update priority
  const updatePriority = (id, priority) => {
    setTodos(prevTodos =>
      prevTodos.map(todo =>
        todo.id === id ? { ...todo, priority } : todo
      )
    );
  };
  
  // Filter todos
  const getFilteredTodos = () => {
    let filtered = todos;
    
    switch (filter) {
      case 'active':
        filtered = todos.filter(todo => !todo.completed);
        break;
      case 'completed':
        filtered = todos.filter(todo => todo.completed);
        break;
      default:
        filtered = todos;
    }
    
    // Sort todos
    return filtered.sort((a, b) => {
      switch (sortBy) {
        case 'priority':
          const priorityOrder = { high: 3, medium: 2, low: 1 };
          return priorityOrder[b.priority] - priorityOrder[a.priority];
        case 'text':
          return a.text.localeCompare(b.text);
        default:
          return new Date(b.createdAt) - new Date(a.createdAt);
      }
    });
  };
  
  const filteredTodos = getFilteredTodos();
  
  return (
    <div className="todo-app">
      <h2>Advanced Todo List</h2>
      
      {/* Add new todo */}
      <div className="add-todo">
        <input
          type="text"
          value={newTodo}
          onChange={(e) => setNewTodo(e.target.value)}
          onKeyPress={(e) => e.key === 'Enter' && addTodo()}
          placeholder="Add a new todo..."
        />
        <button onClick={addTodo}>Add</button>
      </div>
      
      {/* Filters and sorting */}
      <div className="controls">
        <div className="filters">
          <button 
            className={filter === 'all' ? 'active' : ''}
            onClick={() => setFilter('all')}
          >
            All ({todos.length})
          </button>
          <button 
            className={filter === 'active' ? 'active' : ''}
            onClick={() => setFilter('active')}
          >
            Active ({todos.filter(t => !t.completed).length})
          </button>
          <button 
            className={filter === 'completed' ? 'active' : ''}
            onClick={() => setFilter('completed')}
          >
            Completed ({todos.filter(t => t.completed).length})
          </button>
        </div>
        
        <div className="sorting">
          <label>Sort by: </label>
          <select value={sortBy} onChange={(e) => setSortBy(e.target.value)}>
            <option value="createdAt">Date Created</option>
            <option value="priority">Priority</option>
            <option value="text">Alphabetical</option>
          </select>
        </div>
      </div>
      
      {/* Todo list */}
      <div className="todo-list">
        {filteredTodos.length === 0 ? (
          <p className="empty-message">No todos found!</p>
        ) : (
          filteredTodos.map(todo => (
            <TodoItem
              key={todo.id} // IMPORTANT: Using unique ID as key
              todo={todo}
              onToggle={toggleTodo}
              onDelete={deleteTodo}
              onUpdate={updateTodo}
              onUpdatePriority={updatePriority}
            />
          ))
        )}
      </div>
      
      {/* Statistics */}
      <div className="stats">
        <p>Total: {todos.length} | Completed: {todos.filter(t => t.completed).length} | Remaining: {todos.filter(t => !t.completed).length}</p>
      </div>
    </div>
  );
}

// Separate component for todo item
function TodoItem({ todo, onToggle, onDelete, onUpdate, onUpdatePriority }) {
  const [isEditing, setIsEditing] = useState(false);
  const [editText, setEditText] = useState(todo.text);
  
  const handleSave = () => {
    if (editText.trim()) {
      onUpdate(todo.id, editText.trim());
      setIsEditing(false);
    }
  };
  
  const handleCancel = () => {
    setEditText(todo.text);
    setIsEditing(false);
  };
  
  const getPriorityColor = (priority) => {
    switch (priority) {
      case 'high': return '#ff4757';
      case 'medium': return '#ffa502';
      case 'low': return '#2ed573';
      default: return '#747d8c';
    }
  };
  
  return (
    <div className={`todo-item ${todo.completed ? 'completed' : ''}`}>
      <input
        type="checkbox"
        checked={todo.completed}
        onChange={() => onToggle(todo.id)}
      />
      
      {isEditing ? (
        <div className="edit-mode">
          <input
            type="text"
            value={editText}
            onChange={(e) => setEditText(e.target.value)}
            onKeyPress={(e) => e.key === 'Enter' && handleSave()}
            autoFocus
          />
          <button onClick={handleSave}>Save</button>
          <button onClick={handleCancel}>Cancel</button>
        </div>
      ) : (
        <div className="view-mode">
          <span className="todo-text">{todo.text}</span>
          <span 
            className="priority-badge"
            style={{ backgroundColor: getPriorityColor(todo.priority) }}
          >
            {todo.priority}
          </span>
          <span className="created-date">
            {todo.createdAt.toLocaleDateString()}
          </span>
        </div>
      )}
      
      <div className="actions">
        {!isEditing && (
          <>
            <select
              value={todo.priority}
              onChange={(e) => onUpdatePriority(todo.id, e.target.value)}
            >
              <option value="low">Low</option>
              <option value="medium">Medium</option>
              <option value="high">High</option>
            </select>
            <button onClick={() => setIsEditing(true)}>Edit</button>
          </>
        )}
        <button onClick={() => onDelete(todo.id)} className="delete-btn">
          Delete
        </button>
      </div>
    </div>
  );
}
```

**Example 2: Nested Lists and Complex Data Structures**
```jsx
function NestedCategoryList() {
  const categories = [
    {
      id: 1,
      name: 'Electronics',
      items: [
        { id: 101, name: 'Laptop', price: 50000, inStock: true },
        { id: 102, name: 'Phone', price: 25000, inStock: false },
        { id: 103, name: 'Tablet', price: 15000, inStock: true }
      ]
    },
    {
      id: 2,
      name: 'Books',
      items: [
        { id: 201, name: 'React Guide', price: 500, inStock: true },
        { id: 202, name: 'JavaScript Basics', price: 400, inStock: true },
        { id: 203, name: 'CSS Mastery', price: 350, inStock: false }
      ]
    },
    {
      id: 3,
      name: 'Clothing',
      items: [
        { id: 301, name: 'T-Shirt', price: 800, inStock: true },
        { id: 302, name: 'Jeans', price: 1500, inStock: true },
        { id: 303, name: 'Jacket', price: 2500, inStock: false }
      ]
    }
  ];
  
  const [expandedCategories, setExpandedCategories] = useState(new Set([1]));
  const [searchTerm, setSearchTerm] = useState('');
  
  const toggleCategory = (categoryId) => {
    setExpandedCategories(prev => {
      const newSet = new Set(prev);
      if (newSet.has(categoryId)) {
        newSet.delete(categoryId);
      } else {
        newSet.add(categoryId);
      }
      return newSet;
    });
  };
  
  const getFilteredCategories = () => {
    if (!searchTerm) return categories;
    
    return categories.map(category => ({
      ...category,
      items: category.items.filter(item =>
        item.name.toLowerCase().includes(searchTerm.toLowerCase())
      )
    })).filter(category => category.items.length > 0);
  };
  
  const filteredCategories = getFilteredCategories();
  
  return (
    <div className="nested-list">
      <h2>Product Categories</h2>
      
      <div className="search">
        <input
          type="text"
          value={searchTerm}
          onChange={(e) => setSearchTerm(e.target.value)}
          placeholder="Search products..."
        />
      </div>
      
      <div className="category-list">
        {filteredCategories.map(category => (
          <div key={category.id} className="category">
            <div 
              className="category-header"
              onClick={() => toggleCategory(category.id)}
            >
              <span className="expand-icon">
                {expandedCategories.has(category.id) ? '▼' : '▶'}
              </span>
              <h3>{category.name}</h3>
              <span className="item-count">({category.items.length} items)</span>
            </div>
            
            {expandedCategories.has(category.id) && (
              <div className="category-items">
                {category.items.map(item => (
                  <div key={item.id} className={`item ${!item.inStock ? 'out-of-stock' : ''}`}>
                    <span className="item-name">{item.name}</span>
                    <span className="item-price">₹{item.price.toLocaleString()}</span>
                    <span className={`stock-status ${item.inStock ? 'in-stock' : 'out-of-stock'}`}>
                      {item.inStock ? '✓ In Stock' : '✗ Out of Stock'}
                    </span>
                  </div>
                ))}
              </div>
            )}
          </div>
        ))}
      </div>
      
      {filteredCategories.length === 0 && (
        <p className="no-results">No products found matching "{searchTerm}"</p>
      )}
    </div>
  );
}
```

**Example 3: Performance Optimization with Keys**
```jsx
function PerformanceDemo() {
  const [items, setItems] = useState([
    { id: 1, name: 'Item 1', value: 10 },
    { id: 2, name: 'Item 2', value: 20 },
    { id: 3, name: 'Item 3', value: 30 }
  ]);
  
  const [useProperKeys, setUseProperKeys] = useState(true);
  
  const addItem = () => {
    const newItem = {
      id: Date.now(),
      name: `Item ${items.length + 1}`,
      value: Math.floor(Math.random() * 100)
    };
    setItems(prev => [newItem, ...prev]); // Add to beginning
  };
  
  const removeItem = (id) => {
    setItems(prev => prev.filter(item => item.id !== id));
  };
  
  const shuffleItems = () => {
    setItems(prev => [...prev].sort(() => Math.random() - 0.5));
  };
  
  return (
    <div className="performance-demo">
      <h2>Keys Performance Demo</h2>
      
      <div className="controls">
        <button onClick={addItem}>Add Item (to beginning)</button>
        <button onClick={shuffleItems}>Shuffle Items</button>
        <label>
          <input
            type="checkbox"
            checked={useProperKeys}
            onChange={(e) => setUseProperKeys(e.target.checked)}
          />
          Use Proper Keys (ID vs Index)
        </label>
      </div>
      
      <div className="demo-explanation">
        <p>
          {useProperKeys 
            ? "✅ Using item.id as key - React can efficiently track items"
            : "❌ Using index as key - React may re-render unnecessarily"
          }
        </p>
      </div>
      
      <div className="item-list">
        {items.map((item, index) => (
          <PerformanceItem
            key={useProperKeys ? item.id : index} // Toggle between proper and improper keys
            item={item}
            onRemove={removeItem}
          />
        ))}
      </div>
    </div>
  );
}

// Component that shows re-render behavior
function PerformanceItem({ item, onRemove }) {
  const [renderCount, setRenderCount] = useState(1);
  const [inputValue, setInputValue] = useState('');
  
  // Track re-renders
  useEffect(() => {
    setRenderCount(prev => prev + 1);
  });
  
  return (
    <div className="performance-item">
      <div className="item-info">
        <span>{item.name}</span>
        <span>Value: {item.value}</span>
        <span className="render-count">Renders: {renderCount}</span>
      </div>
      
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
        placeholder="Type here to see re-render behavior"
      />
      
      <button onClick={() => onRemove(item.id)}>Remove</button>
    </div>
  );
}
```

**Key Best Practices and Anti-patterns:**
```jsx
function KeyExamples() {
  const users = [
    { id: 'user_1', name: 'Raj' },
    { id: 'user_2', name: 'Priya' },
    { id: 'user_3', name: 'Amit' }
  ];
  
  return (
    <div>
      {/* ✅ GOOD: Using unique, stable ID */}
      {users.map(user => (
        <div key={user.id}>{user.name}</div>
      ))}
      
      {/* ❌ BAD: Using array index (problematic when order changes) */}
      {users.map((user, index) => (
        <div key={index}>{user.name}</div>
      ))}
      
      {/* ❌ BAD: Using random values */}
      {users.map(user => (
        <div key={Math.random()}>{user.name}</div>
      ))}
      
      {/* ✅ GOOD: Combining multiple fields for uniqueness */}
      {users.map(user => (
        <div key={`${user.id}-${user.name}`}>{user.name}</div>
      ))}
      
      {/* ✅ ACCEPTABLE: Using index when list is static and order never changes */}
      {['Apple', 'Banana', 'Orange'].map((fruit, index) => (
        <div key={index}>{fruit}</div>
      ))}
    </div>
  );
}
```

**Interview Questions:**
1. Why are keys important in React lists?
2. What happens if you don't provide keys in a list?
3. Can you use array index as a key? When is it acceptable?
4. What makes a good key vs a bad key?
5. How do keys help with performance optimization?
6. What is the difference between using index vs unique ID as keys?
7. How do you handle lists with duplicate values?
8. What happens when you use random values as keys?
9. How do you optimize rendering of large lists?
10. What is the key prop and why can't you access it in the component?

---#
## 🔹 Day 13–14: Forms in React - DEEP DIVE

**Definition (English):**
Forms in React are handled through controlled components where form data is managed by React state rather than the DOM. This approach provides better control over form validation, submission, and user interactions. React forms can be controlled (state-managed) or uncontrolled (DOM-managed), with controlled being the preferred approach.

**Hinglish Deep Explanation:**
React mein forms handle karna matlab form ke har input field ka data React state mein store karna. Isse hume form validation, submission, aur user interactions par better control milta hai. Controlled components mein React state form data ko manage karta hai, jabki uncontrolled mein DOM directly handle karta hai.

**Forms Deep Understanding:**

**1. Basic Controlled Forms:**
```jsx
function BasicForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    age: '',
    gender: '',
    country: 'India',
    hobbies: [],
    newsletter: false,
    comments: ''
  });
  
  // Generic handler for all input types
  const handleInputChange = (event) => {
    const { name, value, type, checked } = event.target;
    
    if (type === 'checkbox') {
      if (name === 'hobbies') {
        // Handle checkbox arrays
        setFormData(prev => ({
          ...prev,
          hobbies: checked 
            ? [...prev.hobbies, value]
            : prev.hobbies.filter(hobby => hobby !== value)
        }));
      } else {
        // Handle single checkbox
        setFormData(prev => ({
          ...prev,
          [name]: checked
        }));
      }
    } else {
      setFormData(prev => ({
        ...prev,
        [name]: value
      }));
    }
  };
  
  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Form submitted:', formData);
  };
  
  return (
    <form onSubmit={handleSubmit} className="basic-form">
      <h2>User Registration Form</h2>
      
      {/* Text Input */}
      <div className="form-group">
        <label htmlFor="name">Name:</label>
        <input
          type="text"
          id="name"
          name="name"
          value={formData.name}
          onChange={handleInputChange}
          placeholder="Enter your name"
          required
        />
      </div>
      
      {/* Email Input */}
      <div className="form-group">
        <label htmlFor="email">Email:</label>
        <input
          type="email"
          id="email"
          name="email"
          value={formData.email}
          onChange={handleInputChange}
          placeholder="Enter your email"
          required
        />
      </div>
      
      {/* Number Input */}
      <div className="form-group">
        <label htmlFor="age">Age:</label>
        <input
          type="number"
          id="age"
          name="age"
          value={formData.age}
          onChange={handleInputChange}
          min="1"
          max="120"
        />
      </div>
      
      {/* Radio Buttons */}
      <div className="form-group">
        <label>Gender:</label>
        <div className="radio-group">
          <label>
            <input
              type="radio"
              name="gender"
              value="male"
              checked={formData.gender === 'male'}
              onChange={handleInputChange}
            />
            Male
          </label>
          <label>
            <input
              type="radio"
              name="gender"
              value="female"
              checked={formData.gender === 'female'}
              onChange={handleInputChange}
            />
            Female
          </label>
          <label>
            <input
              type="radio"
              name="gender"
              value="other"
              checked={formData.gender === 'other'}
              onChange={handleInputChange}
            />
            Other
          </label>
        </div>
      </div>
      
      {/* Select Dropdown */}
      <div className="form-group">
        <label htmlFor="country">Country:</label>
        <select
          id="country"
          name="country"
          value={formData.country}
          onChange={handleInputChange}
        >
          <option value="India">India</option>
          <option value="USA">USA</option>
          <option value="UK">UK</option>
          <option value="Canada">Canada</option>
          <option value="Australia">Australia</option>
        </select>
      </div>
      
      {/* Multiple Checkboxes */}
      <div className="form-group">
        <label>Hobbies:</label>
        <div className="checkbox-group">
          {['Reading', 'Gaming', 'Sports', 'Music', 'Travel'].map(hobby => (
            <label key={hobby}>
              <input
                type="checkbox"
                name="hobbies"
                value={hobby}
                checked={formData.hobbies.includes(hobby)}
                onChange={handleInputChange}
              />
              {hobby}
            </label>
          ))}
        </div>
      </div>
      
      {/* Single Checkbox */}
      <div className="form-group">
        <label>
          <input
            type="checkbox"
            name="newsletter"
            checked={formData.newsletter}
            onChange={handleInputChange}
          />
          Subscribe to newsletter
        </label>
      </div>
      
      {/* Textarea */}
      <div className="form-group">
        <label htmlFor="comments">Comments:</label>
        <textarea
          id="comments"
          name="comments"
          value={formData.comments}
          onChange={handleInputChange}
          placeholder="Any additional comments..."
          rows="4"
        />
      </div>
      
      <button type="submit">Submit</button>
      
      {/* Debug: Show current form state */}
      <div className="debug-info">
        <h3>Current Form Data:</h3>
        <pre>{JSON.stringify(formData, null, 2)}</pre>
      </div>
    </form>
  );
}
```

**Example 1: Advanced Form with Validation**
```jsx
function AdvancedForm() {
  const [formData, setFormData] = useState({
    firstName: '',
    lastName: '',
    email: '',
    password: '',
    confirmPassword: '',
    phone: '',
    dateOfBirth: '',
    website: '',
    bio: '',
    skills: [],
    experience: '',
    salary: '',
    agreeToTerms: false
  });
  
  const [errors, setErrors] = useState({});
  const [touched, setTouched] = useState({});
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [submitStatus, setSubmitStatus] = useState(null);
  
  // Validation rules
  const validationRules = {
    firstName: {
      required: true,
      minLength: 2,
      pattern: /^[a-zA-Z\s]+$/,
      message: 'First name must be at least 2 characters and contain only letters'
    },
    lastName: {
      required: true,
      minLength: 2,
      pattern: /^[a-zA-Z\s]+$/,
      message: 'Last name must be at least 2 characters and contain only letters'
    },
    email: {
      required: true,
      pattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
      message: 'Please enter a valid email address'
    },
    password: {
      required: true,
      minLength: 8,
      pattern: /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]/,
      message: 'Password must be at least 8 characters with uppercase, lowercase, number, and special character'
    },
    phone: {
      required: true,
      pattern: /^[6-9]\d{9}$/,
      message: 'Please enter a valid 10-digit Indian mobile number'
    },
    website: {
      required: false,
      pattern: /^https?:\/\/.+\..+/,
      message: 'Please enter a valid URL (http:// or https://)'
    }
  };
  
  // Validate single field
  const validateField = (name, value) => {
    const rule = validationRules[name];
    if (!rule) return '';
    
    if (rule.required && !value.trim()) {
      return `${name} is required`;
    }
    
    if (value && rule.minLength && value.length < rule.minLength) {
      return `${name} must be at least ${rule.minLength} characters`;
    }
    
    if (value && rule.pattern && !rule.pattern.test(value)) {
      return rule.message;
    }
    
    // Custom validations
    if (name === 'confirmPassword' && value !== formData.password) {
      return 'Passwords do not match';
    }
    
    if (name === 'dateOfBirth') {
      const age = new Date().getFullYear() - new Date(value).getFullYear();
      if (age < 18) {
        return 'You must be at least 18 years old';
      }
    }
    
    return '';
  };
  
  // Handle input changes
  const handleInputChange = (event) => {
    const { name, value, type, checked } = event.target;
    
    let newValue = value;
    if (type === 'checkbox') {
      if (name === 'skills') {
        newValue = checked 
          ? [...formData.skills, value]
          : formData.skills.filter(skill => skill !== value);
      } else {
        newValue = checked;
      }
    }
    
    setFormData(prev => ({
      ...prev,
      [name]: newValue
    }));
    
    // Real-time validation
    if (touched[name]) {
      const error = validateField(name, newValue);
      setErrors(prev => ({
        ...prev,
        [name]: error
      }));
    }
  };
  
  // Handle field blur (when user leaves field)
  const handleBlur = (event) => {
    const { name, value } = event.target;
    
    setTouched(prev => ({
      ...prev,
      [name]: true
    }));
    
    const error = validateField(name, value);
    setErrors(prev => ({
      ...prev,
      [name]: error
    }));
  };
  
  // Validate entire form
  const validateForm = () => {
    const newErrors = {};
    
    Object.keys(validationRules).forEach(field => {
      const error = validateField(field, formData[field]);
      if (error) {
        newErrors[field] = error;
      }
    });
    
    // Additional validations
    if (!formData.agreeToTerms) {
      newErrors.agreeToTerms = 'You must agree to the terms and conditions';
    }
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };
  
  // Handle form submission
  const handleSubmit = async (event) => {
    event.preventDefault();
    
    // Mark all fields as touched
    const allTouched = {};
    Object.keys(formData).forEach(key => {
      allTouched[key] = true;
    });
    setTouched(allTouched);
    
    if (!validateForm()) {
      setSubmitStatus('error');
      return;
    }
    
    setIsSubmitting(true);
    setSubmitStatus(null);
    
    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 2000));
      
      console.log('Form submitted successfully:', formData);
      setSubmitStatus('success');
      
      // Reset form
      setFormData({
        firstName: '',
        lastName: '',
        email: '',
        password: '',
        confirmPassword: '',
        phone: '',
        dateOfBirth: '',
        website: '',
        bio: '',
        skills: [],
        experience: '',
        salary: '',
        agreeToTerms: false
      });
      setTouched({});
      setErrors({});
      
    } catch (error) {
      console.error('Submission error:', error);
      setSubmitStatus('error');
    } finally {
      setIsSubmitting(false);
    }
  };
  
  return (
    <form onSubmit={handleSubmit} className="advanced-form">
      <h2>Professional Registration Form</h2>
      
      {submitStatus === 'success' && (
        <div className="success-message">
          ✅ Registration successful! Welcome aboard.
        </div>
      )}
      
      {submitStatus === 'error' && (
        <div className="error-message">
          ❌ Please fix the errors below and try again.
        </div>
      )}
      
      <div className="form-row">
        <div className="form-group">
          <label htmlFor="firstName">First Name *</label>
          <input
            type="text"
            id="firstName"
            name="firstName"
            value={formData.firstName}
            onChange={handleInputChange}
            onBlur={handleBlur}
            className={errors.firstName ? 'error' : ''}
            placeholder="Enter first name"
          />
          {errors.firstName && <span className="error-text">{errors.firstName}</span>}
        </div>
        
        <div className="form-group">
          <label htmlFor="lastName">Last Name *</label>
          <input
            type="text"
            id="lastName"
            name="lastName"
            value={formData.lastName}
            onChange={handleInputChange}
            onBlur={handleBlur}
            className={errors.lastName ? 'error' : ''}
            placeholder="Enter last name"
          />
          {errors.lastName && <span className="error-text">{errors.lastName}</span>}
        </div>
      </div>
      
      <div className="form-group">
        <label htmlFor="email">Email Address *</label>
        <input
          type="email"
          id="email"
          name="email"
          value={formData.email}
          onChange={handleInputChange}
          onBlur={handleBlur}
          className={errors.email ? 'error' : ''}
          placeholder="Enter email address"
        />
        {errors.email && <span className="error-text">{errors.email}</span>}
      </div>
      
      <div className="form-row">
        <div className="form-group">
          <label htmlFor="password">Password *</label>
          <input
            type="password"
            id="password"
            name="password"
            value={formData.password}
            onChange={handleInputChange}
            onBlur={handleBlur}
            className={errors.password ? 'error' : ''}
            placeholder="Enter password"
          />
          {errors.password && <span className="error-text">{errors.password}</span>}
        </div>
        
        <div className="form-group">
          <label htmlFor="confirmPassword">Confirm Password *</label>
          <input
            type="password"
            id="confirmPassword"
            name="confirmPassword"
            value={formData.confirmPassword}
            onChange={handleInputChange}
            onBlur={handleBlur}
            className={errors.confirmPassword ? 'error' : ''}
            placeholder="Confirm password"
          />
          {errors.confirmPassword && <span className="error-text">{errors.confirmPassword}</span>}
        </div>
      </div>
      
      <div className="form-row">
        <div className="form-group">
          <label htmlFor="phone">Phone Number *</label>
          <input
            type="tel"
            id="phone"
            name="phone"
            value={formData.phone}
            onChange={handleInputChange}
            onBlur={handleBlur}
            className={errors.phone ? 'error' : ''}
            placeholder="Enter 10-digit mobile number"
          />
          {errors.phone && <span className="error-text">{errors.phone}</span>}
        </div>
        
        <div className="form-group">
          <label htmlFor="dateOfBirth">Date of Birth *</label>
          <input
            type="date"
            id="dateOfBirth"
            name="dateOfBirth"
            value={formData.dateOfBirth}
            onChange={handleInputChange}
            onBlur={handleBlur}
            className={errors.dateOfBirth ? 'error' : ''}
          />
          {errors.dateOfBirth && <span className="error-text">{errors.dateOfBirth}</span>}
        </div>
      </div>
      
      <div className="form-group">
        <label htmlFor="website">Website (Optional)</label>
        <input
          type="url"
          id="website"
          name="website"
          value={formData.website}
          onChange={handleInputChange}
          onBlur={handleBlur}
          className={errors.website ? 'error' : ''}
          placeholder="https://example.com"
        />
        {errors.website && <span className="error-text">{errors.website}</span>}
      </div>
      
      <div className="form-group">
        <label>Skills</label>
        <div className="checkbox-group">
          {['JavaScript', 'React', 'Node.js', 'Python', 'Java', 'CSS', 'HTML'].map(skill => (
            <label key={skill}>
              <input
                type="checkbox"
                name="skills"
                value={skill}
                checked={formData.skills.includes(skill)}
                onChange={handleInputChange}
              />
              {skill}
            </label>
          ))}
        </div>
      </div>
      
      <div className="form-group">
        <label htmlFor="experience">Experience Level</label>
        <select
          id="experience"
          name="experience"
          value={formData.experience}
          onChange={handleInputChange}
        >
          <option value="">Select experience level</option>
          <option value="fresher">Fresher (0-1 years)</option>
          <option value="junior">Junior (1-3 years)</option>
          <option value="mid">Mid-level (3-5 years)</option>
          <option value="senior">Senior (5+ years)</option>
        </select>
      </div>
      
      <div className="form-group">
        <label htmlFor="salary">Expected Salary (₹ per annum)</label>
        <input
          type="number"
          id="salary"
          name="salary"
          value={formData.salary}
          onChange={handleInputChange}
          placeholder="e.g., 500000"
          min="0"
        />
      </div>
      
      <div className="form-group">
        <label htmlFor="bio">Bio</label>
        <textarea
          id="bio"
          name="bio"
          value={formData.bio}
          onChange={handleInputChange}
          placeholder="Tell us about yourself..."
          rows="4"
          maxLength="500"
        />
        <small>{formData.bio.length}/500 characters</small>
      </div>
      
      <div className="form-group">
        <label>
          <input
            type="checkbox"
            name="agreeToTerms"
            checked={formData.agreeToTerms}
            onChange={handleInputChange}
          />
          I agree to the <a href="/terms" target="_blank">Terms and Conditions</a> *
        </label>
        {errors.agreeToTerms && <span className="error-text">{errors.agreeToTerms}</span>}
      </div>
      
      <button 
        type="submit" 
        disabled={isSubmitting}
        className="submit-button"
      >
        {isSubmitting ? 'Submitting...' : 'Register'}
      </button>
    </form>
  );
}
```

**Example 2: Dynamic Forms and Field Arrays**
```jsx
function DynamicForm() {
  const [formData, setFormData] = useState({
    companyName: '',
    employees: [
      { id: 1, name: '', position: '', salary: '' }
    ],
    projects: [
      { id: 1, title: '', description: '', technologies: [] }
    ]
  });
  
  // Add new employee
  const addEmployee = () => {
    const newEmployee = {
      id: Date.now(),
      name: '',
      position: '',
      salary: ''
    };
    setFormData(prev => ({
      ...prev,
      employees: [...prev.employees, newEmployee]
    }));
  };
  
  // Remove employee
  const removeEmployee = (id) => {
    setFormData(prev => ({
      ...prev,
      employees: prev.employees.filter(emp => emp.id !== id)
    }));
  };
  
  // Update employee
  const updateEmployee = (id, field, value) => {
    setFormData(prev => ({
      ...prev,
      employees: prev.employees.map(emp =>
        emp.id === id ? { ...emp, [field]: value } : emp
      )
    }));
  };
  
  // Add new project
  const addProject = () => {
    const newProject = {
      id: Date.now(),
      title: '',
      description: '',
      technologies: []
    };
    setFormData(prev => ({
      ...prev,
      projects: [...prev.projects, newProject]
    }));
  };
  
  // Remove project
  const removeProject = (id) => {
    setFormData(prev => ({
      ...prev,
      projects: prev.projects.filter(proj => proj.id !== id)
    }));
  };
  
  // Update project
  const updateProject = (id, field, value) => {
    setFormData(prev => ({
      ...prev,
      projects: prev.projects.map(proj =>
        proj.id === id ? { ...proj, [field]: value } : proj
      )
    }));
  };
  
  // Update project technologies
  const updateProjectTechnology = (projectId, technology, checked) => {
    setFormData(prev => ({
      ...prev,
      projects: prev.projects.map(proj => {
        if (proj.id === projectId) {
          const technologies = checked
            ? [...proj.technologies, technology]
            : proj.technologies.filter(tech => tech !== technology);
          return { ...proj, technologies };
        }
        return proj;
      })
    }));
  };
  
  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Dynamic form submitted:', formData);
  };
  
  const availableTechnologies = ['React', 'Node.js', 'Python', 'Java', 'MongoDB', 'PostgreSQL'];
  
  return (
    <form onSubmit={handleSubmit} className="dynamic-form">
      <h2>Company Information Form</h2>
      
      <div className="form-group">
        <label htmlFor="companyName">Company Name</label>
        <input
          type="text"
          id="companyName"
          value={formData.companyName}
          onChange={(e) => setFormData(prev => ({ ...prev, companyName: e.target.value }))}
          placeholder="Enter company name"
        />
      </div>
      
      {/* Dynamic Employee Section */}
      <div className="section">
        <div className="section-header">
          <h3>Employees</h3>
          <button type="button" onClick={addEmployee}>Add Employee</button>
        </div>
        
        {formData.employees.map((employee, index) => (
          <div key={employee.id} className="dynamic-item">
            <div className="item-header">
              <h4>Employee {index + 1}</h4>
              {formData.employees.length > 1 && (
                <button 
                  type="button" 
                  onClick={() => removeEmployee(employee.id)}
                  className="remove-button"
                >
                  Remove
                </button>
              )}
            </div>
            
            <div className="form-row">
              <div className="form-group">
                <label>Name</label>
                <input
                  type="text"
                  value={employee.name}
                  onChange={(e) => updateEmployee(employee.id, 'name', e.target.value)}
                  placeholder="Employee name"
                />
              </div>
              
              <div className="form-group">
                <label>Position</label>
                <input
                  type="text"
                  value={employee.position}
                  onChange={(e) => updateEmployee(employee.id, 'position', e.target.value)}
                  placeholder="Job position"
                />
              </div>
              
              <div className="form-group">
                <label>Salary</label>
                <input
                  type="number"
                  value={employee.salary}
                  onChange={(e) => updateEmployee(employee.id, 'salary', e.target.value)}
                  placeholder="Annual salary"
                />
              </div>
            </div>
          </div>
        ))}
      </div>
      
      {/* Dynamic Projects Section */}
      <div className="section">
        <div className="section-header">
          <h3>Projects</h3>
          <button type="button" onClick={addProject}>Add Project</button>
        </div>
        
        {formData.projects.map((project, index) => (
          <div key={project.id} className="dynamic-item">
            <div className="item-header">
              <h4>Project {index + 1}</h4>
              {formData.projects.length > 1 && (
                <button 
                  type="button" 
                  onClick={() => removeProject(project.id)}
                  className="remove-button"
                >
                  Remove
                </button>
              )}
            </div>
            
            <div className="form-group">
              <label>Project Title</label>
              <input
                type="text"
                value={project.title}
                onChange={(e) => updateProject(project.id, 'title', e.target.value)}
                placeholder="Project title"
              />
            </div>
            
            <div className="form-group">
              <label>Description</label>
              <textarea
                value={project.description}
                onChange={(e) => updateProject(project.id, 'description', e.target.value)}
                placeholder="Project description"
                rows="3"
              />
            </div>
            
            <div className="form-group">
              <label>Technologies Used</label>
              <div className="checkbox-group">
                {availableTechnologies.map(tech => (
                  <label key={tech}>
                    <input
                      type="checkbox"
                      checked={project.technologies.includes(tech)}
                      onChange={(e) => updateProjectTechnology(project.id, tech, e.target.checked)}
                    />
                    {tech}
                  </label>
                ))}
              </div>
            </div>
          </div>
        ))}
      </div>
      
      <button type="submit" className="submit-button">
        Submit Company Information
      </button>
      
      {/* Debug Information */}
      <div className="debug-section">
        <h3>Form Data Preview:</h3>
        <pre>{JSON.stringify(formData, null, 2)}</pre>
      </div>
    </form>
  );
}
```

**Example 3: Uncontrolled Components with useRef**
```jsx
function UncontrolledForm() {
  const nameRef = useRef();
  const emailRef = useRef();
  const fileRef = useRef();
  const [submittedData, setSubmittedData] = useState(null);
  
  const handleSubmit = (event) => {
    event.preventDefault();
    
    const formData = {
      name: nameRef.current.value,
      email: emailRef.current.value,
      file: fileRef.current.files[0]
    };
    
    setSubmittedData(formData);
    console.log('Uncontrolled form data:', formData);
  };
  
  const resetForm = () => {
    nameRef.current.value = '';
    emailRef.current.value = '';
    fileRef.current.value = '';
    setSubmittedData(null);
  };
  
  return (
    <div className="uncontrolled-form">
      <h2>Uncontrolled Form Example</h2>
      
      <form onSubmit={handleSubmit}>
        <div className="form-group">
          <label htmlFor="name">Name:</label>
          <input
            type="text"
            id="name"
            ref={nameRef}
            defaultValue="John Doe"
            placeholder="Enter your name"
          />
        </div>
        
        <div className="form-group">
          <label htmlFor="email">Email:</label>
          <input
            type="email"
            id="email"
            ref={emailRef}
            placeholder="Enter your email"
          />
        </div>
        
        <div className="form-group">
          <label htmlFor="file">Upload File:</label>
          <input
            type="file"
            id="file"
            ref={fileRef}
            accept=".pdf,.doc,.docx"
          />
        </div>
        
        <div className="form-actions">
          <button type="submit">Submit</button>
          <button type="button" onClick={resetForm}>Reset</button>
        </div>
      </form>
      
      {submittedData && (
        <div className="submitted-data">
          <h3>Submitted Data:</h3>
          <p><strong>Name:</strong> {submittedData.name}</p>
          <p><strong>Email:</strong> {submittedData.email}</p>
          <p><strong>File:</strong> {submittedData.file ? submittedData.file.name : 'No file selected'}</p>
        </div>
      )}
    </div>
  );
}
```

**Form Patterns and Best Practices:**
```jsx
// Custom hook for form handling
function useForm(initialValues, validationRules) {
  const [values, setValues] = useState(initialValues);
  const [errors, setErrors] = useState({});
  const [touched, setTouched] = useState({});
  
  const handleChange = (event) => {
    const { name, value, type, checked } = event.target;
    const newValue = type === 'checkbox' ? checked : value;
    
    setValues(prev => ({
      ...prev,
      [name]: newValue
    }));
    
    // Clear error when user starts typing
    if (errors[name]) {
      setErrors(prev => ({
        ...prev,
        [name]: ''
      }));
    }
  };
  
  const handleBlur = (event) => {
    const { name } = event.target;
    setTouched(prev => ({
      ...prev,
      [name]: true
    }));
    
    // Validate field on blur
    validateField(name);
  };
  
  const validateField = (name) => {
    const rule = validationRules[name];
    const value = values[name];
    
    if (rule && rule.required && !value) {
      setErrors(prev => ({
        ...prev,
        [name]: `${name} is required`
      }));
      return false;
    }
    
    return true;
  };
  
  const validateForm = () => {
    const newErrors = {};
    let isValid = true;
    
    Object.keys(validationRules).forEach(field => {
      if (!validateField(field)) {
        isValid = false;
      }
    });
    
    return isValid;
  };
  
  const resetForm = () => {
    setValues(initialValues);
    setErrors({});
    setTouched({});
  };
  
  return {
    values,
    errors,
    touched,
    handleChange,
    handleBlur,
    validateForm,
    resetForm
  };
}

// Usage of custom hook
function FormWithCustomHook() {
  const {
    values,
    errors,
    touched,
    handleChange,
    handleBlur,
    validateForm,
    resetForm
  } = useForm(
    { name: '', email: '' },
    { name: { required: true }, email: { required: true } }
  );
  
  const handleSubmit = (event) => {
    event.preventDefault();
    if (validateForm()) {
      console.log('Form is valid:', values);
    }
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input
        name="name"
        value={values.name}
        onChange={handleChange}
        onBlur={handleBlur}
        placeholder="Name"
      />
      {touched.name && errors.name && <span>{errors.name}</span>}
      
      <input
        name="email"
        value={values.email}
        onChange={handleChange}
        onBlur={handleBlur}
        placeholder="Email"
      />
      {touched.email && errors.email && <span>{errors.email}</span>}
      
      <button type="submit">Submit</button>
      <button type="button" onClick={resetForm}>Reset</button>
    </form>
  );
}
```

**Interview Questions:**
1. What is the difference between controlled and uncontrolled components?
2. How do you handle form validation in React?
3. What are the advantages of controlled components?
4. How do you handle multiple input types in a single form?
5. What is the purpose of the `name` attribute in form inputs?
6. How do you prevent default form submission behavior?
7. What are some best practices for form handling in React?
8. How do you handle file uploads in React forms?
9. What is the difference between `value` and `defaultValue`?
10. How do you create reusable form components?

---###
 🔹 Day 15–16: Component Lifecycle - DEEP DIVE

**Definition (English):**
Component lifecycle refers to the series of phases a React component goes through from creation to destruction. In class components, lifecycle methods like componentDidMount, componentDidUpdate, and componentWillUnmount handle different phases. In functional components, the useEffect hook manages all lifecycle behaviors, providing a more unified approach to side effects and lifecycle management.

**Hinglish Deep Explanation:**
Component lifecycle matlab component ka birth se death tak ka journey. Class components mein alag-alag methods hote hain har phase ke liye (mount, update, unmount), lekin functional components mein useEffect hook se sab kuch handle karte hain. useEffect bahut powerful hai - ye mounting, updating, aur unmounting sabko handle kar sakta hai.

**Lifecycle Deep Understanding:**

**1. Class Component Lifecycle (Legacy but Important):**
```jsx
class LifecycleDemo extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
      data: null,
      error: null
    };
    console.log('1. Constructor called');
  }
  
  // Mounting Phase
  static getDerivedStateFromProps(props, state) {
    console.log('2. getDerivedStateFromProps called');
    // Return new state or null
    return null;
  }
  
  componentDidMount() {
    console.log('3. componentDidMount called');
    // Perfect place for:
    // - API calls
    // - Setting up subscriptions
    // - DOM manipulation
    this.fetchData();
    this.timer = setInterval(() => {
      this.setState(prev => ({ count: prev.count + 1 }));
    }, 1000);
  }
  
  // Updating Phase
  shouldComponentUpdate(nextProps, nextState) {
    console.log('4. shouldComponentUpdate called');
    // Return true/false to control re-rendering
    // Use for performance optimization
    return nextState.count !== this.state.count;
  }
  
  getSnapshotBeforeUpdate(prevProps, prevState) {
    console.log('5. getSnapshotBeforeUpdate called');
    // Capture some information from DOM before update
    // Return value is passed to componentDidUpdate
    return { scrollPosition: window.scrollY };
  }
  
  componentDidUpdate(prevProps, prevState, snapshot) {
    console.log('6. componentDidUpdate called');
    console.log('Snapshot:', snapshot);
    
    // Perfect place for:
    // - API calls based on prop/state changes
    // - DOM updates
    if (prevState.count !== this.state.count) {
      console.log(`Count changed from ${prevState.count} to ${this.state.count}`);
    }
  }
  
  // Unmounting Phase
  componentWillUnmount() {
    console.log('7. componentWillUnmount called');
    // Cleanup:
    // - Clear timers
    // - Cancel API requests
    // - Remove event listeners
    clearInterval(this.timer);
  }
  
  // Error Handling
  static getDerivedStateFromError(error) {
    console.log('Error caught:', error);
    return { error: error.message };
  }
  
  componentDidCatch(error, errorInfo) {
    console.log('componentDidCatch:', error, errorInfo);
    // Log error to service
  }
  
  fetchData = async () => {
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
      const data = await response.json();
      this.setState({ data });
    } catch (error) {
      this.setState({ error: error.message });
    }
  }
  
  render() {
    console.log('Render called');
    
    if (this.state.error) {
      return <div>Error: {this.state.error}</div>;
    }
    
    return (
      <div>
        <h2>Class Component Lifecycle</h2>
        <p>Count: {this.state.count}</p>
        {this.state.data && (
          <div>
            <h3>Fetched Data:</h3>
            <p>{this.state.data.title}</p>
          </div>
        )}
      </div>
    );
  }
}
```

**2. useEffect Hook - Complete Guide:**
```jsx
function UseEffectDemo() {
  const [count, setCount] = useState(0);
  const [name, setName] = useState('');
  const [posts, setPosts] = useState([]);
  const [loading, setLoading] = useState(false);
  
  // 1. Effect with no dependencies - runs after every render
  useEffect(() => {
    console.log('Effect runs after every render');
    document.title = `Count: ${count}`;
  });
  
  // 2. Effect with empty dependency array - runs only once (componentDidMount)
  useEffect(() => {
    console.log('Effect runs only once - like componentDidMount');
    
    // Setup
    const timer = setInterval(() => {
      console.log('Timer tick');
    }, 1000);
    
    // Cleanup function (componentWillUnmount)
    return () => {
      console.log('Cleanup - like componentWillUnmount');
      clearInterval(timer);
    };
  }, []); // Empty dependency array
  
  // 3. Effect with specific dependencies - runs when dependencies change
  useEffect(() => {
    console.log('Effect runs when count changes');
    
    if (count > 0) {
      localStorage.setItem('count', count.toString());
    }
  }, [count]); // Runs only when count changes
  
  // 4. Effect for API calls with dependency
  useEffect(() => {
    if (name.length > 2) {
      setLoading(true);
      
      // Simulate API call
      const fetchUserPosts = async () => {
        try {
          const response = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${name.length}`);
          const data = await response.json();
          setPosts(data.slice(0, 3)); // Get first 3 posts
        } catch (error) {
          console.error('Error fetching posts:', error);
        } finally {
          setLoading(false);
        }
      };
      
      const timeoutId = setTimeout(fetchUserPosts, 500); // Debounce
      
      // Cleanup previous timeout
      return () => clearTimeout(timeoutId);
    } else {
      setPosts([]);
    }
  }, [name]);
  
  // 5. Effect with cleanup for event listeners
  useEffect(() => {
    const handleResize = () => {
      console.log('Window resized:', window.innerWidth);
    };
    
    const handleScroll = () => {
      console.log('Page scrolled:', window.scrollY);
    };
    
    window.addEventListener('resize', handleResize);
    window.addEventListener('scroll', handleScroll);
    
    // Cleanup
    return () => {
      window.removeEventListener('resize', handleResize);
      window.removeEventListener('scroll', handleScroll);
    };
  }, []);
  
  return (
    <div>
      <h2>useEffect Hook Demo</h2>
      
      <div>
        <p>Count: {count}</p>
        <button onClick={() => setCount(count + 1)}>Increment</button>
        <button onClick={() => setCount(count - 1)}>Decrement</button>
      </div>
      
      <div>
        <input
          type="text"
          value={name}
          onChange={(e) => setName(e.target.value)}
          placeholder="Type name (3+ chars to fetch posts)"
        />
      </div>
      
      {loading && <p>Loading posts...</p>}
      
      {posts.length > 0 && (
        <div>
          <h3>Posts:</h3>
          {posts.map(post => (
            <div key={post.id}>
              <h4>{post.title}</h4>
              <p>{post.body.substring(0, 100)}...</p>
            </div>
          ))}
        </div>
      )}
    </div>
  );
}
```

**Example 1: Advanced useEffect Patterns**
```jsx
function AdvancedEffectPatterns() {
  const [user, setUser] = useState(null);
  const [posts, setPosts] = useState([]);
  const [comments, setComments] = useState([]);
  const [selectedPost, setSelectedPost] = useState(null);
  const [online, setOnline] = useState(navigator.onLine);
  
  // Custom hook for online status
  useEffect(() => {
    const handleOnline = () => setOnline(true);
    const handleOffline = () => setOnline(false);
    
    window.addEventListener('online', handleOnline);
    window.addEventListener('offline', handleOffline);
    
    return () => {
      window.removeEventListener('online', handleOnline);
      window.removeEventListener('offline', handleOffline);
    };
  }, []);
  
  // Fetch user data on mount
  useEffect(() => {
    let cancelled = false;
    
    const fetchUser = async () => {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
        const userData = await response.json();
        
        if (!cancelled) {
          setUser(userData);
        }
      } catch (error) {
        if (!cancelled) {
          console.error('Error fetching user:', error);
        }
      }
    };
    
    fetchUser();
    
    // Cleanup to prevent state update if component unmounts
    return () => {
      cancelled = true;
    };
  }, []);
  
  // Fetch posts when user is loaded
  useEffect(() => {
    if (!user) return;
    
    let cancelled = false;
    
    const fetchPosts = async () => {
      try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${user.id}`);
        const postsData = await response.json();
        
        if (!cancelled) {
          setPosts(postsData);
        }
      } catch (error) {
        if (!cancelled) {
          console.error('Error fetching posts:', error);
        }
      }
    };
    
    fetchPosts();
    
    return () => {
      cancelled = true;
    };
  }, [user]); // Depends on user
  
  // Fetch comments when a post is selected
  useEffect(() => {
    if (!selectedPost) {
      setComments([]);
      return;
    }
    
    let cancelled = false;
    
    const fetchComments = async () => {
      try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/comments?postId=${selectedPost.id}`);
        const commentsData = await response.json();
        
        if (!cancelled) {
          setComments(commentsData);
        }
      } catch (error) {
        if (!cancelled) {
          console.error('Error fetching comments:', error);
        }
      }
    };
    
    fetchComments();
    
    return () => {
      cancelled = true;
    };
  }, [selectedPost]);
  
  // Auto-save selected post to localStorage
  useEffect(() => {
    if (selectedPost) {
      localStorage.setItem('selectedPost', JSON.stringify(selectedPost));
    }
  }, [selectedPost]);
  
  // Load selected post from localStorage on mount
  useEffect(() => {
    const savedPost = localStorage.getItem('selectedPost');
    if (savedPost) {
      try {
        const parsedPost = JSON.parse(savedPost);
        setSelectedPost(parsedPost);
      } catch (error) {
        console.error('Error parsing saved post:', error);
      }
    }
  }, []);
  
  return (
    <div className="advanced-effects">
      <div className="status-bar">
        <span className={`status ${online ? 'online' : 'offline'}`}>
          {online ? '🟢 Online' : '🔴 Offline'}
        </span>
      </div>
      
      {user && (
        <div className="user-info">
          <h2>Welcome, {user.name}!</h2>
          <p>Email: {user.email}</p>
        </div>
      )}
      
      <div className="posts-section">
        <h3>Posts ({posts.length})</h3>
        {posts.map(post => (
          <div 
            key={post.id} 
            className={`post ${selectedPost?.id === post.id ? 'selected' : ''}`}
            onClick={() => setSelectedPost(post)}
          >
            <h4>{post.title}</h4>
            <p>{post.body.substring(0, 100)}...</p>
          </div>
        ))}
      </div>
      
      {selectedPost && (
        <div className="comments-section">
          <h3>Comments for: {selectedPost.title}</h3>
          {comments.map(comment => (
            <div key={comment.id} className="comment">
              <h5>{comment.name}</h5>
              <p><strong>{comment.email}</strong></p>
              <p>{comment.body}</p>
            </div>
          ))}
        </div>
      )}
    </div>
  );
}
```

**Example 2: Custom Hooks for Lifecycle Logic**
```jsx
// Custom hook for API calls
function useApi(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    let cancelled = false;
    
    const fetchData = async () => {
      try {
        setLoading(true);
        setError(null);
        
        const response = await fetch(url);
        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const result = await response.json();
        
        if (!cancelled) {
          setData(result);
        }
      } catch (err) {
        if (!cancelled) {
          setError(err.message);
        }
      } finally {
        if (!cancelled) {
          setLoading(false);
        }
      }
    };
    
    fetchData();
    
    return () => {
      cancelled = true;
    };
  }, [url]);
  
  return { data, loading, error };
}

// Custom hook for local storage
function useLocalStorage(key, initialValue) {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error('Error reading from localStorage:', error);
      return initialValue;
    }
  });
  
  const setValue = (value) => {
    try {
      setStoredValue(value);
      window.localStorage.setItem(key, JSON.stringify(value));
    } catch (error) {
      console.error('Error writing to localStorage:', error);
    }
  };
  
  return [storedValue, setValue];
}

// Custom hook for window size
function useWindowSize() {
  const [windowSize, setWindowSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight
  });
  
  useEffect(() => {
    const handleResize = () => {
      setWindowSize({
        width: window.innerWidth,
        height: window.innerHeight
      });
    };
    
    window.addEventListener('resize', handleResize);
    
    return () => window.removeEventListener('resize', handleResize);
  }, []);
  
  return windowSize;
}

// Custom hook for previous value
function usePrevious(value) {
  const ref = useRef();
  
  useEffect(() => {
    ref.current = value;
  });
  
  return ref.current;
}

// Component using custom hooks
function CustomHooksDemo() {
  const [userId, setUserId] = useLocalStorage('selectedUserId', 1);
  const { data: user, loading, error } = useApi(`https://jsonplaceholder.typicode.com/users/${userId}`);
  const windowSize = useWindowSize();
  const previousUserId = usePrevious(userId);
  
  return (
    <div className="custom-hooks-demo">
      <h2>Custom Hooks Demo</h2>
      
      <div className="window-info">
        <p>Window Size: {windowSize.width} x {windowSize.height}</p>
        <p>Device: {windowSize.width < 768 ? 'Mobile' : 'Desktop'}</p>
      </div>
      
      <div className="user-selector">
        <label>Select User ID:</label>
        <select 
          value={userId} 
          onChange={(e) => setUserId(parseInt(e.target.value))}
        >
          {[1, 2, 3, 4, 5].map(id => (
            <option key={id} value={id}>User {id}</option>
          ))}
        </select>
        {previousUserId && (
          <p>Previous User ID: {previousUserId}</p>
        )}
      </div>
      
      {loading && <p>Loading user data...</p>}
      {error && <p>Error: {error}</p>}
      {user && (
        <div className="user-details">
          <h3>{user.name}</h3>
          <p>Email: {user.email}</p>
          <p>Phone: {user.phone}</p>
          <p>Website: {user.website}</p>
          <p>Company: {user.company.name}</p>
        </div>
      )}
    </div>
  );
}
```

**Example 3: Effect Dependencies and Optimization**
```jsx
function EffectOptimization() {
  const [count, setCount] = useState(0);
  const [multiplier, setMultiplier] = useState(2);
  const [items, setItems] = useState([]);
  
  // ❌ Bad: Missing dependencies
  useEffect(() => {
    console.log('Count is:', count);
    // This effect should depend on count but doesn't list it
  }, []); // ESLint will warn about this
  
  // ✅ Good: Proper dependencies
  useEffect(() => {
    console.log('Count is:', count);
  }, [count]);
  
  // ❌ Bad: Object/function in dependency array
  const config = { multiplier }; // This creates new object on every render
  useEffect(() => {
    console.log('Config changed:', config);
  }, [config]); // This will run on every render
  
  // ✅ Good: Primitive values in dependency array
  useEffect(() => {
    const config = { multiplier };
    console.log('Multiplier changed:', config);
  }, [multiplier]); // Only runs when multiplier changes
  
  // ✅ Good: Using useCallback for function dependencies
  const calculateResult = useCallback(() => {
    return count * multiplier;
  }, [count, multiplier]);
  
  useEffect(() => {
    const result = calculateResult();
    console.log('Calculated result:', result);
  }, [calculateResult]);
  
  // ✅ Good: Conditional effects
  useEffect(() => {
    if (count > 0) {
      document.title = `Count: ${count}`;
    }
  }, [count]);
  
  // ✅ Good: Effect with cleanup for subscriptions
  useEffect(() => {
    const subscription = {
      unsubscribe: () => console.log('Unsubscribed')
    };
    
    // Simulate subscription
    console.log('Subscribed to updates');
    
    return () => {
      subscription.unsubscribe();
    };
  }, []);
  
  // ✅ Good: Debounced effect
  useEffect(() => {
    const timeoutId = setTimeout(() => {
      console.log('Debounced count update:', count);
    }, 500);
    
    return () => clearTimeout(timeoutId);
  }, [count]);
  
  return (
    <div className="effect-optimization">
      <h2>Effect Optimization Examples</h2>
      
      <div>
        <p>Count: {count}</p>
        <button onClick={() => setCount(count + 1)}>Increment</button>
        <button onClick={() => setCount(count - 1)}>Decrement</button>
      </div>
      
      <div>
        <p>Multiplier: {multiplier}</p>
        <button onClick={() => setMultiplier(multiplier + 1)}>Increase Multiplier</button>
      </div>
      
      <div>
        <p>Result: {count * multiplier}</p>
      </div>
    </div>
  );
}
```

**Common useEffect Patterns:**
```jsx
function CommonPatterns() {
  const [data, setData] = useState(null);
  
  // Pattern 1: Fetch data on mount
  useEffect(() => {
    fetch('/api/data')
      .then(res => res.json())
      .then(setData);
  }, []);
  
  // Pattern 2: Cleanup subscriptions
  useEffect(() => {
    const subscription = subscribe();
    return () => subscription.unsubscribe();
  }, []);
  
  // Pattern 3: Update document title
  useEffect(() => {
    document.title = `Page - ${data?.title || 'Loading'}`;
  }, [data]);
  
  // Pattern 4: Set up event listeners
  useEffect(() => {
    const handleKeyPress = (e) => {
      if (e.key === 'Escape') {
        // Handle escape key
      }
    };
    
    document.addEventListener('keydown', handleKeyPress);
    return () => document.removeEventListener('keydown', handleKeyPress);
  }, []);
  
  // Pattern 5: Interval/Timer
  useEffect(() => {
    const interval = setInterval(() => {
      // Do something periodically
    }, 1000);
    
    return () => clearInterval(interval);
  }, []);
  
  return <div>Common useEffect Patterns</div>;
}
```

**Interview Questions:**
1. What are the different phases of React component lifecycle?
2. What is the difference between componentDidMount and useEffect?
3. How do you cleanup side effects in useEffect?
4. What happens if you don't provide a dependency array to useEffect?
5. How do you prevent useEffect from running on every render?
6. What is the purpose of the cleanup function in useEffect?
7. How do you handle async operations in useEffect?
8. What are the rules for useEffect dependencies?
9. How do you optimize useEffect performance?
10. What is the difference between useEffect and useLayoutEffect?

---###
 🔹 Day 17–18: Conditional Rendering - DEEP DIVE

**Definition (English):**
Conditional rendering in React means displaying different UI elements or components based on certain conditions, state values, or props. React provides several techniques for conditional rendering including ternary operators, logical AND (&&) operator, if-else statements, and switch cases. This allows for dynamic user interfaces that respond to application state and user interactions.

**Hinglish Deep Explanation:**
Conditional rendering ka matlab hai ki alag-alag conditions ke basis par alag-alag UI dikhana. Jaise agar user login hai to dashboard dikhana, nahi to login form dikhana. React mein ye karne ke kayi tarike hain - ternary operator (?:), logical AND (&&), if-else statements, aur switch cases. Ye bahut powerful feature hai jo dynamic UIs banane mein help karta hai.

**Conditional Rendering Deep Understanding:**

**1. Basic Conditional Rendering Techniques:**
```jsx
function ConditionalBasics() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [userRole, setUserRole] = useState('guest'); // guest, user, admin
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const [data, setData] = useState(null);
  
  // 1. Ternary Operator (most common)
  const renderAuthButton = () => {
    return isLoggedIn ? (
      <button onClick={() => setIsLoggedIn(false)}>Logout</button>
    ) : (
      <button onClick={() => setIsLoggedIn(true)}>Login</button>
    );
  };
  
  // 2. Logical AND operator (for simple show/hide)
  const renderWelcomeMessage = () => {
    return (
      <div>
        {isLoggedIn && <h2>Welcome back!</h2>}
        {!isLoggedIn && <h2>Please log in to continue</h2>}
      </div>
    );
  };
  
  // 3. If-else with early return
  const renderUserDashboard = () => {
    if (loading) {
      return <div className="loading">Loading...</div>;
    }
    
    if (error) {
      return <div className="error">Error: {error}</div>;
    }
    
    if (!isLoggedIn) {
      return <div className="login-prompt">Please log in to view dashboard</div>;
    }
    
    return (
      <div className="dashboard">
        <h3>User Dashboard</h3>
        <p>Welcome to your personalized dashboard!</p>
      </div>
    );
  };
  
  // 4. Switch case for multiple conditions
  const renderRoleBasedContent = () => {
    switch (userRole) {
      case 'admin':
        return (
          <div className="admin-panel">
            <h3>Admin Panel</h3>
            <button>Manage Users</button>
            <button>System Settings</button>
            <button>View Reports</button>
          </div>
        );
      case 'user':
        return (
          <div className="user-content">
            <h3>User Content</h3>
            <button>View Profile</button>
            <button>My Orders</button>
          </div>
        );
      case 'guest':
      default:
        return (
          <div className="guest-content">
            <h3>Guest Access</h3>
            <p>Limited features available. Please register for full access.</p>
            <button>Register Now</button>
          </div>
        );
    }
  };
  
  // 5. Complex nested conditions
  const renderComplexCondition = () => {
    return (
      <div>
        {isLoggedIn ? (
          userRole === 'admin' ? (
            <div className="admin-welcome">
              <h2>Admin Dashboard</h2>
              {data ? (
                <div>Data loaded: {data.length} items</div>
              ) : (
                <button onClick={() => setData([1, 2, 3])}>Load Data</button>
              )}
            </div>
          ) : (
            <div className="user-welcome">
              <h2>User Dashboard</h2>
              <p>Welcome, regular user!</p>
            </div>
          )
        ) : (
          <div className="login-section">
            <h2>Please Login</h2>
            <p>Access your account to continue</p>
          </div>
        )}
      </div>
    );
  };
  
  return (
    <div className="conditional-basics">
      <h2>Conditional Rendering Basics</h2>
      
      <div className="controls">
        <label>
          <input
            type="checkbox"
            checked={isLoggedIn}
            onChange={(e) => setIsLoggedIn(e.target.checked)}
          />
          Logged In
        </label>
        
        <select value={userRole} onChange={(e) => setUserRole(e.target.value)}>
          <option value="guest">Guest</option>
          <option value="user">User</option>
          <option value="admin">Admin</option>
        </select>
        
        <button onClick={() => setLoading(!loading)}>
          Toggle Loading
        </button>
        
        <button onClick={() => setError(error ? null : 'Sample error occurred')}>
          Toggle Error
        </button>
      </div>
      
      <div className="render-sections">
        <section>
          <h3>1. Ternary Operator:</h3>
          {renderAuthButton()}
        </section>
        
        <section>
          <h3>2. Logical AND:</h3>
          {renderWelcomeMessage()}
        </section>
        
        <section>
          <h3>3. If-else with Early Return:</h3>
          {renderUserDashboard()}
        </section>
        
        <section>
          <h3>4. Switch Case:</h3>
          {renderRoleBasedContent()}
        </section>
        
        <section>
          <h3>5. Complex Nested Conditions:</h3>
          {renderComplexCondition()}
        </section>
      </div>
    </div>
  );
}
```

**Example 1: Advanced Conditional Rendering with State Management**
```jsx
function AdvancedConditionalApp() {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const [view, setView] = useState('home'); // home, profile, settings, admin
  const [notifications, setNotifications] = useState([]);
  const [theme, setTheme] = useState('light');
  const [permissions, setPermissions] = useState([]);
  
  // Simulate login
  const handleLogin = async (userType) => {
    setLoading(true);
    setError(null);
    
    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 1000));
      
      const userData = {
        id: Date.now(),
        name: userType === 'admin' ? 'Admin User' : 'Regular User',
        email: `${userType}@example.com`,
        role: userType,
        avatar: `https://ui-avatars.com/api/?name=${userType}&background=random`,
        preferences: { theme: 'light', notifications: true }
      };
      
      const userPermissions = userType === 'admin' 
        ? ['read', 'write', 'delete', 'admin'] 
        : ['read', 'write'];
      
      setUser(userData);
      setPermissions(userPermissions);
      setNotifications([
        { id: 1, message: 'Welcome back!', type: 'success' },
        { id: 2, message: 'You have 3 new messages', type: 'info' }
      ]);
      
    } catch (err) {
      setError('Login failed. Please try again.');
    } finally {
      setLoading(false);
    }
  };
  
  const handleLogout = () => {
    setUser(null);
    setPermissions([]);
    setNotifications([]);
    setView('home');
  };
  
  // Permission-based rendering
  const hasPermission = (permission) => {
    return permissions.includes(permission);
  };
  
  // Render loading state
  if (loading) {
    return (
      <div className="loading-container">
        <div className="spinner"></div>
        <p>Authenticating...</p>
      </div>
    );
  }
  
  // Render error state
  if (error) {
    return (
      <div className="error-container">
        <h2>❌ Error</h2>
        <p>{error}</p>
        <button onClick={() => setError(null)}>Try Again</button>
      </div>
    );
  }
  
  // Main app render with conditional sections
  return (
    <div className={`app ${theme}`}>
      <header className="app-header">
        <h1>Advanced Conditional App</h1>
        
        {/* Conditional navigation based on auth status */}
        <nav>
          {user ? (
            <div className="nav-authenticated">
              <button 
                className={view === 'home' ? 'active' : ''}
                onClick={() => setView('home')}
              >
                Home
              </button>
              <button 
                className={view === 'profile' ? 'active' : ''}
                onClick={() => setView('profile')}
              >
                Profile
              </button>
              <button 
                className={view === 'settings' ? 'active' : ''}
                onClick={() => setView('settings')}
              >
                Settings
              </button>
              
              {/* Admin-only navigation */}
              {hasPermission('admin') && (
                <button 
                  className={view === 'admin' ? 'active' : ''}
                  onClick={() => setView('admin')}
                >
                  Admin Panel
                </button>
              )}
              
              <div className="user-menu">
                <img src={user.avatar} alt={user.name} className="avatar" />
                <span>{user.name}</span>
                <button onClick={handleLogout}>Logout</button>
              </div>
            </div>
          ) : (
            <div className="nav-guest">
              <button onClick={() => handleLogin('user')}>Login as User</button>
              <button onClick={() => handleLogin('admin')}>Login as Admin</button>
            </div>
          )}
        </nav>
        
        {/* Conditional notifications */}
        {notifications.length > 0 && (
          <div className="notifications">
            {notifications.map(notification => (
              <div key={notification.id} className={`notification ${notification.type}`}>
                {notification.message}
                <button onClick={() => setNotifications(prev => 
                  prev.filter(n => n.id !== notification.id)
                )}>×</button>
              </div>
            ))}
          </div>
        )}
      </header>
      
      <main className="app-main">
        {/* Conditional main content based on auth and view */}
        {!user ? (
          <div className="welcome-section">
            <h2>Welcome to Our App</h2>
            <p>Please log in to access your personalized dashboard.</p>
            <div className="features">
              <div className="feature">
                <h3>🔒 Secure</h3>
                <p>Your data is protected with enterprise-grade security.</p>
              </div>
              <div className="feature">
                <h3>⚡ Fast</h3>
                <p>Lightning-fast performance for the best user experience.</p>
              </div>
              <div className="feature">
                <h3>🎨 Beautiful</h3>
                <p>Clean, modern interface designed for productivity.</p>
              </div>
            </div>
          </div>
        ) : (
          <div className="authenticated-content">
            {/* Conditional content based on current view */}
            {view === 'home' && (
              <div className="home-view">
                <h2>Dashboard</h2>
                <div className="dashboard-stats">
                  <div className="stat-card">
                    <h3>Welcome back, {user.name}!</h3>
                    <p>Role: {user.role}</p>
                  </div>
                  <div className="stat-card">
                    <h3>Quick Actions</h3>
                    {hasPermission('write') && <button>Create New</button>}
                    {hasPermission('admin') && <button>Manage Users</button>}
                  </div>
                </div>
              </div>
            )}
            
            {view === 'profile' && (
              <div className="profile-view">
                <h2>Profile</h2>
                <div className="profile-info">
                  <img src={user.avatar} alt={user.name} className="profile-avatar" />
                  <div className="profile-details">
                    <h3>{user.name}</h3>
                    <p>Email: {user.email}</p>
                    <p>Role: {user.role}</p>
                    <p>Permissions: {permissions.join(', ')}</p>
                  </div>
                </div>
                
                {hasPermission('write') && (
                  <div className="profile-actions">
                    <button>Edit Profile</button>
                    <button>Change Password</button>
                  </div>
                )}
              </div>
            )}
            
            {view === 'settings' && (
              <div className="settings-view">
                <h2>Settings</h2>
                <div className="settings-group">
                  <h3>Appearance</h3>
                  <label>
                    Theme:
                    <select value={theme} onChange={(e) => setTheme(e.target.value)}>
                      <option value="light">Light</option>
                      <option value="dark">Dark</option>
                    </select>
                  </label>
                </div>
                
                <div className="settings-group">
                  <h3>Notifications</h3>
                  <label>
                    <input type="checkbox" defaultChecked />
                    Email notifications
                  </label>
                  <label>
                    <input type="checkbox" defaultChecked />
                    Push notifications
                  </label>
                </div>
                
                {/* Admin-only settings */}
                {hasPermission('admin') && (
                  <div className="settings-group">
                    <h3>Admin Settings</h3>
                    <button>System Configuration</button>
                    <button>User Management</button>
                    <button>Security Settings</button>
                  </div>
                )}
              </div>
            )}
            
            {/* Admin-only view */}
            {view === 'admin' && hasPermission('admin') && (
              <div className="admin-view">
                <h2>Admin Panel</h2>
                <div className="admin-sections">
                  <div className="admin-card">
                    <h3>User Management</h3>
                    <p>Manage user accounts and permissions</p>
                    <button>View Users</button>
                  </div>
                  <div className="admin-card">
                    <h3>System Stats</h3>
                    <p>Monitor system performance and usage</p>
                    <button>View Stats</button>
                  </div>
                  <div className="admin-card">
                    <h3>Security</h3>
                    <p>Configure security settings and policies</p>
                    <button>Security Settings</button>
                  </div>
                </div>
              </div>
            )}
            
            {/* Fallback for unauthorized admin access */}
            {view === 'admin' && !hasPermission('admin') && (
              <div className="unauthorized">
                <h2>🚫 Access Denied</h2>
                <p>You don't have permission to access this section.</p>
                <button onClick={() => setView('home')}>Go to Home</button>
              </div>
            )}
          </div>
        )}
      </main>
    </div>
  );
}
```

**Example 2: Conditional Rendering with Complex Business Logic**
```jsx
function ECommerceConditionalApp() {
  const [user, setUser] = useState(null);
  const [cart, setCart] = useState([]);
  const [products, setProducts] = useState([
    { id: 1, name: 'Laptop', price: 50000, stock: 5, category: 'electronics' },
    { id: 2, name: 'Book', price: 500, stock: 0, category: 'books' },
    { id: 3, name: 'Shirt', price: 1000, stock: 10, category: 'clothing' }
  ]);
  const [selectedCategory, setSelectedCategory] = useState('all');
  const [priceRange, setPriceRange] = useState({ min: 0, max: 100000 });
  const [showOutOfStock, setShowOutOfStock] = useState(false);
  
  // Complex filtering logic
  const getFilteredProducts = () => {
    return products.filter(product => {
      const categoryMatch = selectedCategory === 'all' || product.category === selectedCategory;
      const priceMatch = product.price >= priceRange.min && product.price <= priceRange.max;
      const stockMatch = showOutOfStock || product.stock > 0;
      
      return categoryMatch && priceMatch && stockMatch;
    });
  };
  
  const addToCart = (product) => {
    if (product.stock > 0) {
      setCart(prev => {
        const existing = prev.find(item => item.id === product.id);
        if (existing) {
          return prev.map(item =>
            item.id === product.id 
              ? { ...item, quantity: item.quantity + 1 }
              : item
          );
        }
        return [...prev, { ...product, quantity: 1 }];
      });
    }
  };
  
  const getTotalPrice = () => {
    return cart.reduce((total, item) => total + (item.price * item.quantity), 0);
  };
  
  const getCartItemCount = () => {
    return cart.reduce((total, item) => total + item.quantity, 0);
  };
  
  // Conditional product card rendering
  const ProductCard = ({ product }) => {
    const isInCart = cart.some(item => item.id === product.id);
    const cartItem = cart.find(item => item.id === product.id);
    const isOutOfStock = product.stock === 0;
    const isLowStock = product.stock > 0 && product.stock <= 2;
    
    return (
      <div className={`product-card ${isOutOfStock ? 'out-of-stock' : ''}`}>
        <h3>{product.name}</h3>
        <p className="price">₹{product.price.toLocaleString()}</p>
        
        {/* Conditional stock status */}
        {isOutOfStock ? (
          <span className="stock-status out-of-stock">Out of Stock</span>
        ) : isLowStock ? (
          <span className="stock-status low-stock">Only {product.stock} left!</span>
        ) : (
          <span className="stock-status in-stock">In Stock ({product.stock})</span>
        )}
        
        {/* Conditional action buttons */}
        <div className="product-actions">
          {isOutOfStock ? (
            <button disabled className="notify-btn">
              Notify When Available
            </button>
          ) : user ? (
            <div>
              <button onClick={() => addToCart(product)}>
                Add to Cart
              </button>
              {isInCart && (
                <span className="cart-indicator">
                  In cart: {cartItem.quantity}
                </span>
              )}
            </div>
          ) : (
            <button onClick={() => alert('Please login to add items to cart')}>
              Login to Purchase
            </button>
          )}
        </div>
        
        {/* Conditional badges */}
        <div className="product-badges">
          {product.price < 1000 && <span className="badge budget">Budget Friendly</span>}
          {isLowStock && <span className="badge urgent">Limited Stock</span>}
          {product.category === 'electronics' && <span className="badge tech">Tech</span>}
        </div>
      </div>
    );
  };
  
  const filteredProducts = getFilteredProducts();
  
  return (
    <div className="ecommerce-app">
      <header className="app-header">
        <h1>E-Commerce Store</h1>
        
        {/* Conditional user section */}
        <div className="user-section">
          {user ? (
            <div className="user-info">
              <span>Welcome, {user.name}!</span>
              <button onClick={() => setUser(null)}>Logout</button>
            </div>
          ) : (
            <button onClick={() => setUser({ name: 'John Doe', id: 1 })}>
              Login
            </button>
          )}
          
          {/* Conditional cart indicator */}
          {cart.length > 0 && (
            <div className="cart-indicator">
              🛒 {getCartItemCount()} items (₹{getTotalPrice().toLocaleString()})
            </div>
          )}
        </div>
      </header>
      
      <div className="app-content">
        <aside className="filters">
          <h3>Filters</h3>
          
          <div className="filter-group">
            <label>Category:</label>
            <select 
              value={selectedCategory} 
              onChange={(e) => setSelectedCategory(e.target.value)}
            >
              <option value="all">All Categories</option>
              <option value="electronics">Electronics</option>
              <option value="books">Books</option>
              <option value="clothing">Clothing</option>
            </select>
          </div>
          
          <div className="filter-group">
            <label>Price Range:</label>
            <input
              type="range"
              min="0"
              max="100000"
              value={priceRange.max}
              onChange={(e) => setPriceRange(prev => ({ ...prev, max: parseInt(e.target.value) }))}
            />
            <span>Up to ₹{priceRange.max.toLocaleString()}</span>
          </div>
          
          <div className="filter-group">
            <label>
              <input
                type="checkbox"
                checked={showOutOfStock}
                onChange={(e) => setShowOutOfStock(e.target.checked)}
              />
              Show out of stock items
            </label>
          </div>
        </aside>
        
        <main className="products-section">
          <div className="products-header">
            <h2>Products</h2>
            <span className="product-count">
              {filteredProducts.length} product{filteredProducts.length !== 1 ? 's' : ''} found
            </span>
          </div>
          
          {/* Conditional products display */}
          {filteredProducts.length === 0 ? (
            <div className="no-products">
              <h3>No products found</h3>
              <p>Try adjusting your filters or search criteria.</p>
              <button onClick={() => {
                setSelectedCategory('all');
                setPriceRange({ min: 0, max: 100000 });
                setShowOutOfStock(true);
              }}>
                Clear Filters
              </button>
            </div>
          ) : (
            <div className="products-grid">
              {filteredProducts.map(product => (
                <ProductCard key={product.id} product={product} />
              ))}
            </div>
          )}
          
          {/* Conditional promotional messages */}
          {!user && filteredProducts.length > 0 && (
            <div className="promo-message">
              <h3>🎉 Special Offer!</h3>
              <p>Login now and get 10% off on your first purchase!</p>
            </div>
          )}
          
          {user && cart.length === 0 && filteredProducts.length > 0 && (
            <div className="empty-cart-message">
              <h3>Your cart is empty</h3>
              <p>Add some products to get started!</p>
            </div>
          )}
          
          {cart.length > 0 && (
            <div className="cart-summary">
              <h3>Cart Summary</h3>
              {cart.map(item => (
                <div key={item.id} className="cart-item">
                  <span>{item.name} x {item.quantity}</span>
                  <span>₹{(item.price * item.quantity).toLocaleString()}</span>
                </div>
              ))}
              <div className="cart-total">
                <strong>Total: ₹{getTotalPrice().toLocaleString()}</strong>
              </div>
              <button className="checkout-btn">Proceed to Checkout</button>
            </div>
          )}
        </main>
      </div>
    </div>
  );
}
```

**Example 3: Conditional Rendering Performance Patterns**
```jsx
function PerformanceOptimizedConditional() {
  const [activeTab, setActiveTab] = useState('dashboard');
  const [user, setUser] = useState({ role: 'user', preferences: { theme: 'light' } });
  const [data, setData] = useState(null);
  
  // ✅ Good: Memoized expensive components
  const ExpensiveDashboard = useMemo(() => {
    if (activeTab !== 'dashboard') return null;
    
    return (
      <div className="dashboard">
        <h2>Dashboard</h2>
        {/* Expensive calculations or large lists */}
        <div>Complex dashboard content...</div>
      </div>
    );
  }, [activeTab]);
  
  // ✅ Good: Conditional component loading
  const LazyAdminPanel = lazy(() => import('./AdminPanel'));
  
  // ✅ Good: Early returns for better performance
  if (!user) {
    return <LoginForm />;
  }
  
  // ✅ Good: Conditional rendering with proper keys
  const renderTabContent = () => {
    switch (activeTab) {
      case 'dashboard':
        return <div key="dashboard">{ExpensiveDashboard}</div>;
      case 'profile':
        return <ProfileComponent key="profile" user={user} />;
      case 'settings':
        return <SettingsComponent key="settings" user={user} />;
      case 'admin':
        return user.role === 'admin' ? (
          <Suspense fallback={<div>Loading admin panel...</div>}>
            <LazyAdminPanel key="admin" />
          </Suspense>
        ) : (
          <div key="unauthorized">Access Denied</div>
        );
      default:
        return <div key="default">Page not found</div>;
    }
  };
  
  return (
    <div className="optimized-app">
      <nav>
        {['dashboard', 'profile', 'settings'].map(tab => (
          <button
            key={tab}
            className={activeTab === tab ? 'active' : ''}
            onClick={() => setActiveTab(tab)}
          >
            {tab.charAt(0).toUpperCase() + tab.slice(1)}
          </button>
        ))}
        {user.role === 'admin' && (
          <button
            className={activeTab === 'admin' ? 'active' : ''}
            onClick={() => setActiveTab('admin')}
          >
            Admin
          </button>
        )}
      </nav>
      
      <main>
        {renderTabContent()}
      </main>
    </div>
  );
}

// Helper components
const LoginForm = () => <div>Please log in</div>;
const ProfileComponent = ({ user }) => <div>Profile for {user.name}</div>;
const SettingsComponent = ({ user }) => <div>Settings for {user.name}</div>;
```

**Common Conditional Rendering Patterns:**
```jsx
// Pattern 1: Null rendering (don't render anything)
{condition && <Component />}
{!condition && null}

// Pattern 2: Default values
{data || 'Loading...'}
{items.length > 0 ? <List items={items} /> : <EmptyState />}

// Pattern 3: Multiple conditions
{loading ? <Spinner /> : error ? <Error /> : <Content />}

// Pattern 4: Permission-based rendering
{hasPermission('read') && <ReadOnlyView />}
{hasPermission('write') && <EditableView />}

// Pattern 5: Feature flags
{features.newDesign ? <NewComponent /> : <OldComponent />}
```

**Interview Questions:**
1. What are the different ways to implement conditional rendering in React?
2. When should you use ternary operator vs logical AND operator?
3. How do you handle multiple conditions in JSX?
4. What are the performance implications of conditional rendering?
5. How do you conditionally render components based on user permissions?
6. What is the difference between conditional rendering and conditional CSS?
7. How do you handle nested conditional rendering?
8. What are some best practices for conditional rendering?
9. How do you test conditional rendering in React components?
10. What happens when you return null from a component?

---### 🔹 Da
y 19–20: Styling in React - DEEP DIVE

**Definition (English):**
Styling in React refers to the various methods and approaches used to apply CSS styles to React components. React supports multiple styling approaches including traditional CSS files, inline styles, CSS Modules, CSS-in-JS libraries (like styled-components, emotion), CSS frameworks (Bootstrap, Tailwind), and CSS preprocessors (Sass, Less). Each approach has its own benefits and use cases.

**Hinglish Deep Explanation:**
React mein styling karne ke bahut saare tarike hain. Traditional CSS files se lekar modern CSS-in-JS solutions tak. Har approach ka apna fayda hai - CSS Modules scope provide karte hain, styled-components dynamic styling dete hain, Tailwind utility classes deta hai. Choice project requirements aur team preferences par depend karti hai.

**Styling Deep Understanding:**

**1. Traditional CSS and CSS Modules:**
```jsx
// Traditional CSS approach
// styles.css
/*
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.header {
  background-color: #f8f9fa;
  border-bottom: 1px solid #dee2e6;
  padding: 1rem 0;
}

.button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.button:hover {
  background-color: #0056b3;
}

.button.disabled {
  background-color: #6c757d;
  cursor: not-allowed;
}
*/

// Component using traditional CSS
import './styles.css';

function TraditionalCSSComponent() {
  const [isDisabled, setIsDisabled] = useState(false);
  
  return (
    <div className="container">
      <header className="header">
        <h1>Traditional CSS Example</h1>
      </header>
      
      <main>
        <button 
          className={`button ${isDisabled ? 'disabled' : ''}`}
          disabled={isDisabled}
          onClick={() => setIsDisabled(!isDisabled)}
        >
          {isDisabled ? 'Disabled' : 'Click me'}
        </button>
      </main>
    </div>
  );
}

// CSS Modules approach
// Button.module.css
/*
.button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.2s ease;
  font-size: 1rem;
  font-weight: 500;
}

.button:hover {
  background-color: #0056b3;
  transform: translateY(-1px);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.primary {
  background-color: #007bff;
}

.secondary {
  background-color: #6c757d;
}

.success {
  background-color: #28a745;
}

.danger {
  background-color: #dc3545;
}

.large {
  padding: 0.75rem 1.5rem;
  font-size: 1.125rem;
}

.small {
  padding: 0.25rem 0.5rem;
  font-size: 0.875rem;
}

.disabled {
  background-color: #e9ecef;
  color: #6c757d;
  cursor: not-allowed;
  transform: none;
}

.disabled:hover {
  background-color: #e9ecef;
  transform: none;
  box-shadow: none;
}
*/

// Component using CSS Modules
import styles from './Button.module.css';

function ModularButton({ 
  children, 
  variant = 'primary', 
  size = 'medium', 
  disabled = false, 
  onClick 
}) {
  const buttonClasses = [
    styles.button,
    styles[variant],
    styles[size],
    disabled && styles.disabled
  ].filter(Boolean).join(' ');
  
  return (
    <button 
      className={buttonClasses}
      disabled={disabled}
      onClick={onClick}
    >
      {children}
    </button>
  );
}

// Usage example
function CSSModulesExample() {
  return (
    <div>
      <h2>CSS Modules Example</h2>
      <div style={{ display: 'flex', gap: '1rem', flexWrap: 'wrap' }}>
        <ModularButton variant="primary">Primary</ModularButton>
        <ModularButton variant="secondary">Secondary</ModularButton>
        <ModularButton variant="success" size="large">Success Large</ModularButton>
        <ModularButton variant="danger" size="small">Danger Small</ModularButton>
        <ModularButton disabled>Disabled</ModularButton>
      </div>
    </div>
  );
}
```

**2. Inline Styles and Dynamic Styling:**
```jsx
function InlineStylesExample() {
  const [theme, setTheme] = useState('light');
  const [isHovered, setIsHovered] = useState(false);
  const [progress, setProgress] = useState(0);
  
  // Theme configurations
  const themes = {
    light: {
      background: '#ffffff',
      color: '#333333',
      cardBackground: '#f8f9fa',
      borderColor: '#dee2e6',
      primaryColor: '#007bff'
    },
    dark: {
      background: '#1a1a1a',
      color: '#ffffff',
      cardBackground: '#2d2d2d',
      borderColor: '#404040',
      primaryColor: '#4dabf7'
    }
  };
  
  const currentTheme = themes[theme];
  
  // Dynamic styles based on state
  const containerStyle = {
    backgroundColor: currentTheme.background,
    color: currentTheme.color,
    minHeight: '100vh',
    padding: '2rem',
    transition: 'all 0.3s ease',
    fontFamily: 'Arial, sans-serif'
  };
  
  const cardStyle = {
    backgroundColor: currentTheme.cardBackground,
    border: `1px solid ${currentTheme.borderColor}`,
    borderRadius: '8px',
    padding: '1.5rem',
    margin: '1rem 0',
    boxShadow: isHovered 
      ? '0 8px 16px rgba(0, 0, 0, 0.1)' 
      : '0 2px 4px rgba(0, 0, 0, 0.05)',
    transform: isHovered ? 'translateY(-2px)' : 'translateY(0)',
    transition: 'all 0.3s ease',
    cursor: 'pointer'
  };
  
  const buttonStyle = {
    backgroundColor: currentTheme.primaryColor,
    color: 'white',
    border: 'none',
    padding: '0.75rem 1.5rem',
    borderRadius: '6px',
    cursor: 'pointer',
    fontSize: '1rem',
    fontWeight: '500',
    transition: 'all 0.2s ease',
    marginRight: '1rem'
  };
  
  const progressBarStyle = {
    width: '100%',
    height: '20px',
    backgroundColor: currentTheme.borderColor,
    borderRadius: '10px',
    overflow: 'hidden',
    margin: '1rem 0'
  };
  
  const progressFillStyle = {
    width: `${progress}%`,
    height: '100%',
    backgroundColor: currentTheme.primaryColor,
    transition: 'width 0.3s ease',
    borderRadius: '10px'
  };
  
  // Responsive styles using JavaScript
  const getResponsiveStyle = () => {
    const width = window.innerWidth;
    if (width < 768) {
      return {
        padding: '1rem',
        fontSize: '0.9rem'
      };
    } else if (width < 1024) {
      return {
        padding: '1.5rem',
        fontSize: '1rem'
      };
    } else {
      return {
        padding: '2rem',
        fontSize: '1.1rem'
      };
    }
  };
  
  const [responsiveStyle, setResponsiveStyle] = useState(getResponsiveStyle());
  
  useEffect(() => {
    const handleResize = () => {
      setResponsiveStyle(getResponsiveStyle());
    };
    
    window.addEventListener('resize', handleResize);
    return () => window.removeEventListener('resize', handleResize);
  }, []);
  
  useEffect(() => {
    const interval = setInterval(() => {
      setProgress(prev => (prev >= 100 ? 0 : prev + 10));
    }, 500);
    
    return () => clearInterval(interval);
  }, []);
  
  return (
    <div style={{ ...containerStyle, ...responsiveStyle }}>
      <h1 style={{ textAlign: 'center', marginBottom: '2rem' }}>
        Inline Styles Example
      </h1>
      
      <div style={{ textAlign: 'center', marginBottom: '2rem' }}>
        <button 
          style={buttonStyle}
          onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}
          onMouseEnter={(e) => {
            e.target.style.transform = 'scale(1.05)';
            e.target.style.boxShadow = '0 4px 8px rgba(0, 0, 0, 0.2)';
          }}
          onMouseLeave={(e) => {
            e.target.style.transform = 'scale(1)';
            e.target.style.boxShadow = 'none';
          }}
        >
          Switch to {theme === 'light' ? 'Dark' : 'Light'} Theme
        </button>
      </div>
      
      <div 
        style={cardStyle}
        onMouseEnter={() => setIsHovered(true)}
        onMouseLeave={() => setIsHovered(false)}
      >
        <h3 style={{ margin: '0 0 1rem 0', color: currentTheme.primaryColor }}>
          Dynamic Card
        </h3>
        <p style={{ margin: '0 0 1rem 0', lineHeight: '1.6' }}>
          This card changes appearance based on hover state and theme. 
          The styles are calculated dynamically using JavaScript.
        </p>
        
        <div>
          <strong>Progress Bar:</strong>
          <div style={progressBarStyle}>
            <div style={progressFillStyle}></div>
          </div>
          <small style={{ color: currentTheme.color, opacity: 0.7 }}>
            {progress}% Complete
          </small>
        </div>
      </div>
      
      <div style={cardStyle}>
        <h3 style={{ margin: '0 0 1rem 0', color: currentTheme.primaryColor }}>
          Responsive Design
        </h3>
        <p style={{ margin: '0', lineHeight: '1.6' }}>
          This layout adapts to different screen sizes using JavaScript-based 
          responsive styling. Current window width: {window.innerWidth}px
        </p>
      </div>
    </div>
  );
}
```

**Example 1: Styled Components (CSS-in-JS)**
```jsx
import styled, { createGlobalStyle, ThemeProvider } from 'styled-components';

// Global styles
const GlobalStyle = createGlobalStyle`
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: ${props => props.theme.colors.text};
    background-color: ${props => props.theme.colors.background};
    transition: all 0.3s ease;
  }
`;

// Theme configuration
const lightTheme = {
  colors: {
    primary: '#007bff',
    secondary: '#6c757d',
    success: '#28a745',
    danger: '#dc3545',
    warning: '#ffc107',
    background: '#ffffff',
    surface: '#f8f9fa',
    text: '#333333',
    textSecondary: '#6c757d',
    border: '#dee2e6'
  },
  spacing: {
    xs: '0.25rem',
    sm: '0.5rem',
    md: '1rem',
    lg: '1.5rem',
    xl: '2rem',
    xxl: '3rem'
  },
  breakpoints: {
    mobile: '768px',
    tablet: '1024px',
    desktop: '1200px'
  }
};

const darkTheme = {
  ...lightTheme,
  colors: {
    ...lightTheme.colors,
    primary: '#4dabf7',
    background: '#1a1a1a',
    surface: '#2d2d2d',
    text: '#ffffff',
    textSecondary: '#adb5bd',
    border: '#404040'
  }
};

// Styled components
const Container = styled.div`
  max-width: 1200px;
  margin: 0 auto;
  padding: ${props => props.theme.spacing.xl};
  
  @media (max-width: ${props => props.theme.breakpoints.mobile}) {
    padding: ${props => props.theme.spacing.md};
  }
`;

const Card = styled.div`
  background-color: ${props => props.theme.colors.surface};
  border: 1px solid ${props => props.theme.colors.border};
  border-radius: 8px;
  padding: ${props => props.theme.spacing.lg};
  margin: ${props => props.theme.spacing.md} 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
  }
  
  ${props => props.featured && `
    border-color: ${props.theme.colors.primary};
    border-width: 2px;
  `}
`;

const Button = styled.button`
  background-color: ${props => {
    switch(props.variant) {
      case 'secondary': return props.theme.colors.secondary;
      case 'success': return props.theme.colors.success;
      case 'danger': return props.theme.colors.danger;
      case 'warning': return props.theme.colors.warning;
      default: return props.theme.colors.primary;
    }
  }};
  color: white;
  border: none;
  padding: ${props => {
    switch(props.size) {
      case 'small': return `${props.theme.spacing.sm} ${props.theme.spacing.md}`;
      case 'large': return `${props.theme.spacing.lg} ${props.theme.spacing.xl}`;
      default: return `${props.theme.spacing.md} ${props.theme.spacing.lg}`;
    }
  }};
  border-radius: 6px;
  cursor: pointer;
  font-size: ${props => {
    switch(props.size) {
      case 'small': return '0.875rem';
      case 'large': return '1.125rem';
      default: return '1rem';
    }
  }};
  font-weight: 500;
  transition: all 0.2s ease;
  margin-right: ${props => props.theme.spacing.sm};
  
  &:hover {
    opacity: 0.9;
    transform: translateY(-1px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }
  
  &:active {
    transform: translateY(0);
  }
  
  &:disabled {
    background-color: ${props => props.theme.colors.border};
    color: ${props => props.theme.colors.textSecondary};
    cursor: not-allowed;
    transform: none;
    
    &:hover {
      opacity: 1;
      transform: none;
      box-shadow: none;
    }
  }
  
  ${props => props.outline && `
    background-color: transparent;
    color: ${props.theme.colors[props.variant] || props.theme.colors.primary};
    border: 2px solid ${props.theme.colors[props.variant] || props.theme.colors.primary};
    
    &:hover {
      background-color: ${props.theme.colors[props.variant] || props.theme.colors.primary};
      color: white;
    }
  `}
`;

const Grid = styled.div`
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: ${props => props.theme.spacing.lg};
  margin: ${props => props.theme.spacing.xl} 0;
  
  @media (max-width: ${props => props.theme.breakpoints.mobile}) {
    grid-template-columns: 1fr;
    gap: ${props => props.theme.spacing.md};
  }
`;

const Title = styled.h1`
  color: ${props => props.theme.colors.primary};
  text-align: center;
  margin-bottom: ${props => props.theme.spacing.xl};
  font-size: 2.5rem;
  font-weight: 700;
  
  @media (max-width: ${props => props.theme.breakpoints.mobile}) {
    font-size: 2rem;
  }
`;

const Badge = styled.span`
  background-color: ${props => props.theme.colors[props.variant] || props.theme.colors.primary};
  color: white;
  padding: ${props => props.theme.spacing.xs} ${props => props.theme.spacing.sm};
  border-radius: 12px;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
`;

// Main component using styled components
function StyledComponentsExample() {
  const [currentTheme, setCurrentTheme] = useState('light');
  const [loading, setLoading] = useState(false);
  
  const theme = currentTheme === 'light' ? lightTheme : darkTheme;
  
  const handleAsyncAction = async () => {
    setLoading(true);
    await new Promise(resolve => setTimeout(resolve, 2000));
    setLoading(false);
  };
  
  return (
    <ThemeProvider theme={theme}>
      <GlobalStyle />
      <Container>
        <Title>Styled Components Example</Title>
        
        <Card>
          <h3>Theme Controls</h3>
          <p>Switch between light and dark themes to see the dynamic styling in action.</p>
          <Button 
            onClick={() => setCurrentTheme(currentTheme === 'light' ? 'dark' : 'light')}
          >
            Switch to {currentTheme === 'light' ? 'Dark' : 'Light'} Theme
          </Button>
        </Card>
        
        <Grid>
          <Card featured>
            <h3>Featured Card <Badge variant="success">New</Badge></h3>
            <p>This is a featured card with special styling. It has a highlighted border and stands out from other cards.</p>
            <Button variant="primary">Primary Action</Button>
            <Button variant="secondary" outline>Secondary</Button>
          </Card>
          
          <Card>
            <h3>Button Variants</h3>
            <p>Different button styles and sizes available:</p>
            <div style={{ marginTop: '1rem' }}>
              <Button variant="primary" size="small">Small</Button>
              <Button variant="success">Success</Button>
              <Button variant="danger" size="large">Large Danger</Button>
              <Button variant="warning" outline>Warning Outline</Button>
              <Button disabled>Disabled</Button>
            </div>
          </Card>
          
          <Card>
            <h3>Async Actions</h3>
            <p>Example of handling loading states with styled components:</p>
            <Button 
              onClick={handleAsyncAction}
              disabled={loading}
            >
              {loading ? 'Loading...' : 'Start Async Action'}
            </Button>
            {loading && <Badge variant="warning">Processing...</Badge>}
          </Card>
        </Grid>
      </Container>
    </ThemeProvider>
  );
}
```

**Example 2: Tailwind CSS Integration**
```jsx
// Tailwind CSS classes example
function TailwindExample() {
  const [isOpen, setIsOpen] = useState(false);
  const [selectedTab, setSelectedTab] = useState('dashboard');
  const [notifications, setNotifications] = useState([
    { id: 1, message: 'New user registered', type: 'info', time: '2 min ago' },
    { id: 2, message: 'Server maintenance scheduled', type: 'warning', time: '1 hour ago' },
    { id: 3, message: 'Backup completed successfully', type: 'success', time: '3 hours ago' }
  ]);
  
  const tabs = [
    { id: 'dashboard', label: 'Dashboard', icon: '📊' },
    { id: 'users', label: 'Users', icon: '👥' },
    { id: 'settings', label: 'Settings', icon: '⚙️' },
    { id: 'analytics', label: 'Analytics', icon: '📈' }
  ];
  
  const getNotificationColor = (type) => {
    switch (type) {
      case 'success': return 'bg-green-100 border-green-500 text-green-700';
      case 'warning': return 'bg-yellow-100 border-yellow-500 text-yellow-700';
      case 'error': return 'bg-red-100 border-red-500 text-red-700';
      default: return 'bg-blue-100 border-blue-500 text-blue-700';
    }
  };
  
  return (
    <div className="min-h-screen bg-gray-50">
      {/* Header */}
      <header className="bg-white shadow-sm border-b border-gray-200">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between items-center h-16">
            <div className="flex items-center">
              <h1 className="text-2xl font-bold text-gray-900">
                Tailwind Dashboard
              </h1>
            </div>
            
            <div className="flex items-center space-x-4">
              {/* Notifications */}
              <div className="relative">
                <button
                  onClick={() => setIsOpen(!isOpen)}
                  className="relative p-2 text-gray-600 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 rounded-full transition-colors duration-200"
                >
                  🔔
                  {notifications.length > 0 && (
                    <span className="absolute -top-1 -right-1 h-5 w-5 bg-red-500 text-white text-xs rounded-full flex items-center justify-center">
                      {notifications.length}
                    </span>
                  )}
                </button>
                
                {/* Dropdown */}
                {isOpen && (
                  <div className="absolute right-0 mt-2 w-80 bg-white rounded-lg shadow-lg border border-gray-200 z-50">
                    <div className="p-4 border-b border-gray-200">
                      <h3 className="text-lg font-semibold text-gray-900">
                        Notifications
                      </h3>
                    </div>
                    <div className="max-h-64 overflow-y-auto">
                      {notifications.map(notification => (
                        <div
                          key={notification.id}
                          className={`p-4 border-l-4 border-b border-gray-100 last:border-b-0 ${getNotificationColor(notification.type)}`}
                        >
                          <p className="text-sm font-medium">
                            {notification.message}
                          </p>
                          <p className="text-xs mt-1 opacity-75">
                            {notification.time}
                          </p>
                        </div>
                      ))}
                    </div>
                    <div className="p-4 border-t border-gray-200">
                      <button className="w-full text-center text-sm text-blue-600 hover:text-blue-800 font-medium">
                        View all notifications
                      </button>
                    </div>
                  </div>
                )}
              </div>
              
              {/* User menu */}
              <div className="flex items-center space-x-3">
                <img
                  className="h-8 w-8 rounded-full object-cover"
                  src="https://ui-avatars.com/api/?name=John+Doe&background=3b82f6&color=fff"
                  alt="User avatar"
                />
                <span className="text-sm font-medium text-gray-700">
                  John Doe
                </span>
              </div>
            </div>
          </div>
        </div>
      </header>
      
      <div className="flex">
        {/* Sidebar */}
        <aside className="w-64 bg-white shadow-sm min-h-screen">
          <nav className="mt-8">
            {tabs.map(tab => (
              <button
                key={tab.id}
                onClick={() => setSelectedTab(tab.id)}
                className={`w-full flex items-center px-6 py-3 text-left text-sm font-medium transition-colors duration-200 ${
                  selectedTab === tab.id
                    ? 'bg-blue-50 text-blue-700 border-r-2 border-blue-700'
                    : 'text-gray-600 hover:text-gray-900 hover:bg-gray-50'
                }`}
              >
                <span className="mr-3 text-lg">{tab.icon}</span>
                {tab.label}
              </button>
            ))}
          </nav>
        </aside>
        
        {/* Main content */}
        <main className="flex-1 p-8">
          <div className="max-w-6xl mx-auto">
            {/* Page header */}
            <div className="mb-8">
              <h2 className="text-3xl font-bold text-gray-900 capitalize">
                {selectedTab}
              </h2>
              <p className="mt-2 text-gray-600">
                Welcome to the {selectedTab} section of your dashboard.
              </p>
            </div>
            
            {/* Stats cards */}
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
              {[
                { title: 'Total Users', value: '12,345', change: '+12%', color: 'blue' },
                { title: 'Revenue', value: '$54,321', change: '+8%', color: 'green' },
                { title: 'Orders', value: '1,234', change: '-3%', color: 'yellow' },
                { title: 'Conversion', value: '3.2%', change: '+0.5%', color: 'purple' }
              ].map((stat, index) => (
                <div
                  key={index}
                  className="bg-white rounded-lg shadow-sm border border-gray-200 p-6 hover:shadow-md transition-shadow duration-200"
                >
                  <div className="flex items-center justify-between">
                    <div>
                      <p className="text-sm font-medium text-gray-600">
                        {stat.title}
                      </p>
                      <p className="text-2xl font-bold text-gray-900 mt-1">
                        {stat.value}
                      </p>
                    </div>
                    <div className={`p-3 rounded-full bg-${stat.color}-100`}>
                      <div className={`w-6 h-6 bg-${stat.color}-500 rounded`}></div>
                    </div>
                  </div>
                  <div className="mt-4">
                    <span className={`text-sm font-medium ${
                      stat.change.startsWith('+') ? 'text-green-600' : 'text-red-600'
                    }`}>
                      {stat.change}
                    </span>
                    <span className="text-sm text-gray-500 ml-1">
                      from last month
                    </span>
                  </div>
                </div>
              ))}
            </div>
            
            {/* Content area */}
            <div className="bg-white rounded-lg shadow-sm border border-gray-200">
              <div className="p-6 border-b border-gray-200">
                <h3 className="text-lg font-semibold text-gray-900">
                  {selectedTab === 'dashboard' && 'Recent Activity'}
                  {selectedTab === 'users' && 'User Management'}
                  {selectedTab === 'settings' && 'Application Settings'}
                  {selectedTab === 'analytics' && 'Analytics Overview'}
                </h3>
              </div>
              
              <div className="p-6">
                {selectedTab === 'dashboard' && (
                  <div className="space-y-4">
                    {[1, 2, 3, 4, 5].map(item => (
                      <div key={item} className="flex items-center space-x-4 p-4 bg-gray-50 rounded-lg">
                        <div className="w-10 h-10 bg-blue-500 rounded-full flex items-center justify-center text-white font-semibold">
                          {item}
                        </div>
                        <div className="flex-1">
                          <p className="text-sm font-medium text-gray-900">
                            Activity item #{item}
                          </p>
                          <p className="text-sm text-gray-500">
                            Description of the activity that occurred recently.
                          </p>
                        </div>
                        <span className="text-sm text-gray-400">
                          {item} hours ago
                        </span>
                      </div>
                    ))}
                  </div>
                )}
                
                {selectedTab !== 'dashboard' && (
                  <div className="text-center py-12">
                    <div className="text-6xl mb-4">
                      {selectedTab === 'users' && '👥'}
                      {selectedTab === 'settings' && '⚙️'}
                      {selectedTab === 'analytics' && '📈'}
                    </div>
                    <h3 className="text-lg font-medium text-gray-900 mb-2">
                      {selectedTab.charAt(0).toUpperCase() + selectedTab.slice(1)} Content
                    </h3>
                    <p className="text-gray-500">
                      This is where the {selectedTab} content would be displayed.
                    </p>
                  </div>
                )}
              </div>
            </div>
          </div>
        </main>
      </div>
    </div>
  );
}
```

**Example 3: SCSS/Sass Integration**
```jsx
// Component using SCSS
// styles.scss
/*
$primary-color: #007bff;
$secondary-color: #6c757d;
$success-color: #28a745;
$danger-color: #dc3545;
$warning-color: #ffc107;

$font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
$border-radius: 8px;
$box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
$transition: all 0.3s ease;

// Mixins
@mixin button-variant($bg-color, $text-color: white) {
  background-color: $bg-color;
  color: $text-color;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: $border-radius;
  cursor: pointer;
  font-family: $font-family;
  font-weight: 500;
  transition: $transition;
  
  &:hover {
    background-color: darken($bg-color, 10%);
    transform: translateY(-1px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
  }
  
  &:active {
    transform: translateY(0);
  }
  
  &:disabled {
    background-color: lighten($bg-color, 30%);
    cursor: not-allowed;
    transform: none;
    
    &:hover {
      background-color: lighten($bg-color, 30%);
      transform: none;
      box-shadow: none;
    }
  }
}

@mixin card {
  background: white;
  border-radius: $border-radius;
  box-shadow: $box-shadow;
  padding: 1.5rem;
  margin: 1rem 0;
  transition: $transition;
  
  &:hover {
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
    transform: translateY(-2px);
  }
}

@mixin responsive($breakpoint) {
  @if $breakpoint == mobile {
    @media (max-width: 768px) { @content; }
  }
  @if $breakpoint == tablet {
    @media (max-width: 1024px) { @content; }
  }
  @if $breakpoint == desktop {
    @media (min-width: 1025px) { @content; }
  }
}

// Component styles
.scss-example {
  font-family: $font-family;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
  
  @include responsive(mobile) {
    padding: 1rem;
  }
  
  &__header {
    text-align: center;
    margin-bottom: 3rem;
    
    h1 {
      color: $primary-color;
      font-size: 2.5rem;
      margin-bottom: 1rem;
      
      @include responsive(mobile) {
        font-size: 2rem;
      }
    }
    
    p {
      color: $secondary-color;
      font-size: 1.1rem;
    }
  }
  
  &__buttons {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    justify-content: center;
    margin-bottom: 2rem;
    
    @include responsive(mobile) {
      flex-direction: column;
      align-items: center;
    }
    
    .btn {
      &--primary {
        @include button-variant($primary-color);
      }
      
      &--secondary {
        @include button-variant($secondary-color);
      }
      
      &--success {
        @include button-variant($success-color);
      }
      
      &--danger {
        @include button-variant($danger-color);
      }
      
      &--warning {
        @include button-variant($warning-color, #333);
      }
    }
  }
  
  &__cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    
    @include responsive(mobile) {
      grid-template-columns: 1fr;
      gap: 1rem;
    }
  }
  
  &__card {
    @include card;
    
    &--featured {
      border: 2px solid $primary-color;
      position: relative;
      
      &::before {
        content: 'Featured';
        position: absolute;
        top: -10px;
        right: 20px;
        background: $primary-color;
        color: white;
        padding: 0.25rem 0.75rem;
        border-radius: $border-radius;
        font-size: 0.75rem;
        font-weight: 600;
        text-transform: uppercase;
      }
    }
    
    h3 {
      color: $primary-color;
      margin-bottom: 1rem;
      font-size: 1.25rem;
    }
    
    p {
      color: #666;
      line-height: 1.6;
      margin-bottom: 1rem;
    }
    
    .card-actions {
      display: flex;
      gap: 0.5rem;
      flex-wrap: wrap;
    }
  }
  
  &__form {
    @include card;
    max-width: 500px;
    margin: 2rem auto;
    
    .form-group {
      margin-bottom: 1.5rem;
      
      label {
        display: block;
        margin-bottom: 0.5rem;
        font-weight: 500;
        color: #333;
      }
      
      input, textarea, select {
        width: 100%;
        padding: 0.75rem;
        border: 1px solid #ddd;
        border-radius: $border-radius;
        font-family: $font-family;
        transition: $transition;
        
        &:focus {
          outline: none;
          border-color: $primary-color;
          box-shadow: 0 0 0 3px rgba($primary-color, 0.1);
        }
        
        &:invalid {
          border-color: $danger-color;
        }
      }
      
      textarea {
        resize: vertical;
        min-height: 100px;
      }
    }
    
    .form-actions {
      display: flex;
      gap: 1rem;
      justify-content: flex-end;
      
      @include responsive(mobile) {
        flex-direction: column;
      }
    }
  }
}
*/

import './styles.scss';

function SCSSExample() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: ''
  });
  
  const handleInputChange = (e) => {
    const { name, value } = e.target;
    setFormData(prev => ({
      ...prev,
      [name]: value
    }));
  };
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Form submitted:', formData);
  };
  
  return (
    <div className="scss-example">
      <header className="scss-example__header">
        <h1>SCSS/Sass Styling Example</h1>
        <p>Demonstrating the power of Sass with mixins, variables, and nesting</p>
      </header>
      
      <div className="scss-example__buttons">
        <button className="btn btn--primary">Primary</button>
        <button className="btn btn--secondary">Secondary</button>
        <button className="btn btn--success">Success</button>
        <button className="btn btn--danger">Danger</button>
        <button className="btn btn--warning">Warning</button>
      </div>
      
      <div className="scss-example__cards">
        <div className="scss-example__card scss-example__card--featured">
          <h3>Featured Card</h3>
          <p>This card uses SCSS mixins and variables for consistent styling across the application.</p>
          <div className="card-actions">
            <button className="btn btn--primary">Learn More</button>
            <button className="btn btn--secondary">Share</button>
          </div>
        </div>
        
        <div className="scss-example__card">
          <h3>Regular Card</h3>
          <p>Standard card component with hover effects and responsive design built with SCSS.</p>
          <div className="card-actions">
            <button className="btn btn--success">Accept</button>
            <button className="btn btn--danger">Decline</button>
          </div>
        </div>
        
        <div className="scss-example__card">
          <h3>Another Card</h3>
          <p>Demonstrating the reusability of SCSS mixins and the power of nested selectors.</p>
          <div className="card-actions">
            <button className="btn btn--warning">Edit</button>
          </div>
        </div>
      </div>
      
      <form className="scss-example__form" onSubmit={handleSubmit}>
        <h3>Contact Form</h3>
        
        <div className="form-group">
          <label htmlFor="name">Name</label>
          <input
            type="text"
            id="name"
            name="name"
            value={formData.name}
            onChange={handleInputChange}
            required
          />
        </div>
        
        <div className="form-group">
          <label htmlFor="email">Email</label>
          <input
            type="email"
            id="email"
            name="email"
            value={formData.email}
            onChange={handleInputChange}
            required
          />
        </div>
        
        <div className="form-group">
          <label htmlFor="message">Message</label>
          <textarea
            id="message"
            name="message"
            value={formData.message}
            onChange={handleInputChange}
            required
          />
        </div>
        
        <div className="form-actions">
          <button type="button" className="btn btn--secondary">Cancel</button>
          <button type="submit" className="btn btn--primary">Send Message</button>
        </div>
      </form>
    </div>
  );
}
```

**Styling Best Practices and Patterns:**
```jsx
// 1. CSS Custom Properties (CSS Variables)
const CSSVariablesExample = () => {
  const [theme, setTheme] = useState('light');
  
  useEffect(() => {
    const root = document.documentElement;
    if (theme === 'dark') {
      root.style.setProperty('--primary-color', '#4dabf7');
      root.style.setProperty('--background-color', '#1a1a1a');
      root.style.setProperty('--text-color', '#ffffff');
    } else {
      root.style.setProperty('--primary-color', '#007bff');
      root.style.setProperty('--background-color', '#ffffff');
      root.style.setProperty('--text-color', '#333333');
    }
  }, [theme]);
  
  return (
    <div style={{
      backgroundColor: 'var(--background-color)',
      color: 'var(--text-color)',
      padding: '2rem',
      minHeight: '100vh'
    }}>
      <h2 style={{ color: 'var(--primary-color)' }}>CSS Variables Example</h2>
      <button 
        onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}
        style={{
          backgroundColor: 'var(--primary-color)',
          color: 'white',
          border: 'none',
          padding: '0.5rem 1rem',
          borderRadius: '4px'
        }}
      >
        Toggle Theme
      </button>
    </div>
  );
};

// 2. Responsive Design Patterns
const ResponsiveComponent = () => {
  const [windowWidth, setWindowWidth] = useState(window.innerWidth);
  
  useEffect(() => {
    const handleResize = () => setWindowWidth(window.innerWidth);
    window.addEventListener('resize', handleResize);
    return () => window.removeEventListener('resize', handleResize);
  }, []);
  
  const isMobile = windowWidth < 768;
  const isTablet = windowWidth >= 768 && windowWidth < 1024;
  const isDesktop = windowWidth >= 1024;
  
  return (
    <div style={{
      display: 'grid',
      gridTemplateColumns: isMobile ? '1fr' : isTablet ? 'repeat(2, 1fr)' : 'repeat(3, 1fr)',
      gap: '1rem',
      padding: '1rem'
    }}>
      {[1, 2, 3, 4, 5, 6].map(item => (
        <div key={item} style={{
          backgroundColor: '#f8f9fa',
          padding: '1rem',
          borderRadius: '8px',
          textAlign: 'center'
        }}>
          Item {item}
        </div>
      ))}
    </div>
  );
};
```

**Interview Questions:**
1. What are the different ways to style React components?
2. What are the advantages and disadvantages of CSS-in-JS?
3. How do CSS Modules help with style scoping?
4. What is the difference between inline styles and CSS classes?
5. How do you implement responsive design in React?
6. What are styled-components and how do they work?
7. How do you handle dynamic styling based on props or state?
8. What are the performance implications of different styling approaches?
9. How do you implement theming in React applications?
10. What are some best practices for organizing CSS in React projects?

---#
# ⚙️ WEEK 5–6: Advanced State Management

### 🔹 Day 21–22: Context API - DEEP DIVE

**Definition (English):**
The Context API is React's built-in solution for sharing state across multiple components without prop drilling. It provides a way to pass data through the component tree without having to pass props down manually at every level. Context consists of a Provider component that supplies the data and Consumer components (or useContext hook) that consume the data.

**Hinglish Deep Explanation:**
Context API React ka built-in state management solution hai jo prop drilling problem solve karta hai. Jab hume deeply nested components mein same data chahiye hota hai, to har level par props pass karna tedious ho jata hai. Context API se hum data ko directly kisi bhi component mein access kar sakte hain bina intermediate components ko involve kiye.

**Context API Deep Understanding:**

**1. Basic Context Setup and Usage:**
```jsx
import React, { createContext, useContext, useState, useReducer } from 'react';

// 1. Create Context
const ThemeContext = createContext();
const UserContext = createContext();

// 2. Create Provider Components
function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');
  const [fontSize, setFontSize] = useState('medium');
  
  const toggleTheme = () => {
    setTheme(prevTheme => prevTheme === 'light' ? 'dark' : 'light');
  };
  
  const changeFontSize = (size) => {
    setFontSize(size);
  };
  
  const themeConfig = {
    light: {
      background: '#ffffff',
      color: '#333333',
      cardBackground: '#f8f9fa',
      borderColor: '#dee2e6'
    },
    dark: {
      background: '#1a1a1a',
      color: '#ffffff',
      cardBackground: '#2d2d2d',
      borderColor: '#404040'
    }
  };
  
  const fontSizes = {
    small: '14px',
    medium: '16px',
    large: '18px'
  };
  
  const value = {
    theme,
    fontSize,
    themeConfig: themeConfig[theme],
    currentFontSize: fontSizes[fontSize],
    toggleTheme,
    changeFontSize
  };
  
  return (
    <ThemeContext.Provider value={value}>
      {children}
    </ThemeContext.Provider>
  );
}

function UserProvider({ children }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  
  const login = async (credentials) => {
    setLoading(true);
    setError(null);
    
    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 1000));
      
      if (credentials.email === 'admin@example.com') {
        setUser({
          id: 1,
          name: 'Admin User',
          email: credentials.email,
          role: 'admin',
          avatar: 'https://ui-avatars.com/api/?name=Admin+User&background=007bff&color=fff'
        });
      } else {
        setUser({
          id: 2,
          name: 'Regular User',
          email: credentials.email,
          role: 'user',
          avatar: 'https://ui-avatars.com/api/?name=Regular+User&background=28a745&color=fff'
        });
      }
    } catch (err) {
      setError('Login failed. Please try again.');
    } finally {
      setLoading(false);
    }
  };
  
  const logout = () => {
    setUser(null);
    setError(null);
  };
  
  const updateProfile = (updates) => {
    setUser(prevUser => ({
      ...prevUser,
      ...updates
    }));
  };
  
  const value = {
    user,
    loading,
    error,
    login,
    logout,
    updateProfile,
    isAuthenticated: !!user,
    isAdmin: user?.role === 'admin'
  };
  
  return (
    <UserContext.Provider value={value}>
      {children}
    </UserContext.Provider>
  );
}

// 3. Custom Hooks for Context
function useTheme() {
  const context = useContext(ThemeContext);
  if (!context) {
    throw new Error('useTheme must be used within a ThemeProvider');
  }
  return context;
}

function useUser() {
  const context = useContext(UserContext);
  if (!context) {
    throw new Error('useUser must be used within a UserProvider');
  }
  return context;
}

// 4. Components using Context
function Header() {
  const { themeConfig, toggleTheme, fontSize, changeFontSize } = useTheme();
  const { user, logout, isAuthenticated } = useUser();
  
  return (
    <header style={{
      backgroundColor: themeConfig.cardBackground,
      borderBottom: `1px solid ${themeConfig.borderColor}`,
      padding: '1rem 2rem',
      display: 'flex',
      justifyContent: 'space-between',
      alignItems: 'center'
    }}>
      <h1 style={{ 
        color: themeConfig.color,
        fontSize: fontSize === 'small' ? '1.5rem' : fontSize === 'large' ? '2rem' : '1.75rem'
      }}>
        Context API Demo
      </h1>
      
      <div style={{ display: 'flex', alignItems: 'center', gap: '1rem' }}>
        <select 
          value={fontSize} 
          onChange={(e) => changeFontSize(e.target.value)}
          style={{
            backgroundColor: themeConfig.background,
            color: themeConfig.color,
            border: `1px solid ${themeConfig.borderColor}`,
            padding: '0.25rem'
          }}
        >
          <option value="small">Small</option>
          <option value="medium">Medium</option>
          <option value="large">Large</option>
        </select>
        
        <button 
          onClick={toggleTheme}
          style={{
            backgroundColor: themeConfig.color,
            color: themeConfig.background,
            border: 'none',
            padding: '0.5rem 1rem',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Toggle Theme
        </button>
        
        {isAuthenticated ? (
          <div style={{ display: 'flex', alignItems: 'center', gap: '0.5rem' }}>
            <img 
              src={user.avatar} 
              alt={user.name}
              style={{ width: '32px', height: '32px', borderRadius: '50%' }}
            />
            <span style={{ color: themeConfig.color }}>{user.name}</span>
            <button 
              onClick={logout}
              style={{
                backgroundColor: '#dc3545',
                color: 'white',
                border: 'none',
                padding: '0.25rem 0.5rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Logout
            </button>
          </div>
        ) : (
          <span style={{ color: themeConfig.color }}>Not logged in</span>
        )}
      </div>
    </header>
  );
}

function LoginForm() {
  const [credentials, setCredentials] = useState({ email: '', password: '' });
  const { login, loading, error } = useUser();
  const { themeConfig, currentFontSize } = useTheme();
  
  const handleSubmit = (e) => {
    e.preventDefault();
    login(credentials);
  };
  
  return (
    <form 
      onSubmit={handleSubmit}
      style={{
        backgroundColor: themeConfig.cardBackground,
        padding: '2rem',
        borderRadius: '8px',
        border: `1px solid ${themeConfig.borderColor}`,
        maxWidth: '400px',
        margin: '2rem auto'
      }}
    >
      <h2 style={{ color: themeConfig.color, fontSize: currentFontSize, marginBottom: '1rem' }}>
        Login
      </h2>
      
      {error && (
        <div style={{
          backgroundColor: '#f8d7da',
          color: '#721c24',
          padding: '0.5rem',
          borderRadius: '4px',
          marginBottom: '1rem'
        }}>
          {error}
        </div>
      )}
      
      <div style={{ marginBottom: '1rem' }}>
        <input
          type="email"
          placeholder="Email (try admin@example.com)"
          value={credentials.email}
          onChange={(e) => setCredentials(prev => ({ ...prev, email: e.target.value }))}
          style={{
            width: '100%',
            padding: '0.5rem',
            backgroundColor: themeConfig.background,
            color: themeConfig.color,
            border: `1px solid ${themeConfig.borderColor}`,
            borderRadius: '4px',
            fontSize: currentFontSize
          }}
          required
        />
      </div>
      
      <div style={{ marginBottom: '1rem' }}>
        <input
          type="password"
          placeholder="Password"
          value={credentials.password}
          onChange={(e) => setCredentials(prev => ({ ...prev, password: e.target.value }))}
          style={{
            width: '100%',
            padding: '0.5rem',
            backgroundColor: themeConfig.background,
            color: themeConfig.color,
            border: `1px solid ${themeConfig.borderColor}`,
            borderRadius: '4px',
            fontSize: currentFontSize
          }}
          required
        />
      </div>
      
      <button 
        type="submit" 
        disabled={loading}
        style={{
          width: '100%',
          padding: '0.75rem',
          backgroundColor: '#007bff',
          color: 'white',
          border: 'none',
          borderRadius: '4px',
          cursor: loading ? 'not-allowed' : 'pointer',
          fontSize: currentFontSize,
          opacity: loading ? 0.6 : 1
        }}
      >
        {loading ? 'Logging in...' : 'Login'}
      </button>
    </form>
  );
}

function Dashboard() {
  const { user, isAdmin } = useUser();
  const { themeConfig, currentFontSize } = useTheme();
  
  if (!user) {
    return <LoginForm />;
  }
  
  return (
    <div style={{
      padding: '2rem',
      backgroundColor: themeConfig.background,
      color: themeConfig.color,
      minHeight: 'calc(100vh - 80px)'
    }}>
      <div style={{
        backgroundColor: themeConfig.cardBackground,
        padding: '2rem',
        borderRadius: '8px',
        border: `1px solid ${themeConfig.borderColor}`,
        marginBottom: '2rem'
      }}>
        <h2 style={{ fontSize: currentFontSize, marginBottom: '1rem' }}>
          Welcome, {user.name}!
        </h2>
        <p style={{ fontSize: currentFontSize }}>
          Role: {user.role}
        </p>
        <p style={{ fontSize: currentFontSize }}>
          Email: {user.email}
        </p>
      </div>
      
      {isAdmin && (
        <div style={{
          backgroundColor: themeConfig.cardBackground,
          padding: '2rem',
          borderRadius: '8px',
          border: `2px solid #007bff`,
          marginBottom: '2rem'
        }}>
          <h3 style={{ fontSize: currentFontSize, color: '#007bff', marginBottom: '1rem' }}>
            Admin Panel
          </h3>
          <p style={{ fontSize: currentFontSize }}>
            You have admin privileges. You can access special features here.
          </p>
        </div>
      )}
      
      <div style={{
        backgroundColor: themeConfig.cardBackground,
        padding: '2rem',
        borderRadius: '8px',
        border: `1px solid ${themeConfig.borderColor}`
      }}>
        <h3 style={{ fontSize: currentFontSize, marginBottom: '1rem' }}>
          Context Features Demonstrated:
        </h3>
        <ul style={{ fontSize: currentFontSize, lineHeight: '1.6' }}>
          <li>Theme switching (light/dark mode)</li>
          <li>Font size preferences</li>
          <li>User authentication state</li>
          <li>Role-based access control</li>
          <li>Global error handling</li>
          <li>Loading states</li>
        </ul>
      </div>
    </div>
  );
}

// Main App Component
function BasicContextApp() {
  return (
    <ThemeProvider>
      <UserProvider>
        <div>
          <Header />
          <Dashboard />
        </div>
      </UserProvider>
    </ThemeProvider>
  );
}
```

**Example 1: Advanced Context with useReducer**
```jsx
// Advanced Context using useReducer for complex state management
const ShoppingCartContext = createContext();

// Action types
const CART_ACTIONS = {
  ADD_ITEM: 'ADD_ITEM',
  REMOVE_ITEM: 'REMOVE_ITEM',
  UPDATE_QUANTITY: 'UPDATE_QUANTITY',
  CLEAR_CART: 'CLEAR_CART',
  APPLY_COUPON: 'APPLY_COUPON',
  REMOVE_COUPON: 'REMOVE_COUPON',
  SET_SHIPPING: 'SET_SHIPPING'
};

// Reducer function
function cartReducer(state, action) {
  switch (action.type) {
    case CART_ACTIONS.ADD_ITEM: {
      const existingItem = state.items.find(item => item.id === action.payload.id);
      
      if (existingItem) {
        return {
          ...state,
          items: state.items.map(item =>
            item.id === action.payload.id
              ? { ...item, quantity: item.quantity + 1 }
              : item
          )
        };
      }
      
      return {
        ...state,
        items: [...state.items, { ...action.payload, quantity: 1 }]
      };
    }
    
    case CART_ACTIONS.REMOVE_ITEM:
      return {
        ...state,
        items: state.items.filter(item => item.id !== action.payload)
      };
    
    case CART_ACTIONS.UPDATE_QUANTITY:
      return {
        ...state,
        items: state.items.map(item =>
          item.id === action.payload.id
            ? { ...item, quantity: Math.max(0, action.payload.quantity) }
            : item
        ).filter(item => item.quantity > 0)
      };
    
    case CART_ACTIONS.CLEAR_CART:
      return {
        ...state,
        items: []
      };
    
    case CART_ACTIONS.APPLY_COUPON:
      return {
        ...state,
        coupon: action.payload
      };
    
    case CART_ACTIONS.REMOVE_COUPON:
      return {
        ...state,
        coupon: null
      };
    
    case CART_ACTIONS.SET_SHIPPING:
      return {
        ...state,
        shipping: action.payload
      };
    
    default:
      return state;
  }
}

// Initial state
const initialCartState = {
  items: [],
  coupon: null,
  shipping: { method: 'standard', cost: 0 }
};

// Cart Provider
function ShoppingCartProvider({ children }) {
  const [state, dispatch] = useReducer(cartReducer, initialCartState);
  
  // Computed values
  const subtotal = state.items.reduce((sum, item) => sum + (item.price * item.quantity), 0);
  const discount = state.coupon ? (subtotal * state.coupon.discount) / 100 : 0;
  const total = subtotal - discount + state.shipping.cost;
  const itemCount = state.items.reduce((sum, item) => sum + item.quantity, 0);
  
  // Actions
  const addItem = (product) => {
    dispatch({ type: CART_ACTIONS.ADD_ITEM, payload: product });
  };
  
  const removeItem = (productId) => {
    dispatch({ type: CART_ACTIONS.REMOVE_ITEM, payload: productId });
  };
  
  const updateQuantity = (productId, quantity) => {
    dispatch({ 
      type: CART_ACTIONS.UPDATE_QUANTITY, 
      payload: { id: productId, quantity } 
    });
  };
  
  const clearCart = () => {
    dispatch({ type: CART_ACTIONS.CLEAR_CART });
  };
  
  const applyCoupon = (coupon) => {
    dispatch({ type: CART_ACTIONS.APPLY_COUPON, payload: coupon });
  };
  
  const removeCoupon = () => {
    dispatch({ type: CART_ACTIONS.REMOVE_COUPON });
  };
  
  const setShipping = (shipping) => {
    dispatch({ type: CART_ACTIONS.SET_SHIPPING, payload: shipping });
  };
  
  const value = {
    ...state,
    subtotal,
    discount,
    total,
    itemCount,
    addItem,
    removeItem,
    updateQuantity,
    clearCart,
    applyCoupon,
    removeCoupon,
    setShipping
  };
  
  return (
    <ShoppingCartContext.Provider value={value}>
      {children}
    </ShoppingCartContext.Provider>
  );
}

// Custom hook
function useShoppingCart() {
  const context = useContext(ShoppingCartContext);
  if (!context) {
    throw new Error('useShoppingCart must be used within a ShoppingCartProvider');
  }
  return context;
}

// Components using the advanced context
function ProductList() {
  const { addItem } = useShoppingCart();
  
  const products = [
    { id: 1, name: 'Laptop', price: 50000, image: '💻' },
    { id: 2, name: 'Phone', price: 25000, image: '📱' },
    { id: 3, name: 'Headphones', price: 5000, image: '🎧' },
    { id: 4, name: 'Watch', price: 15000, image: '⌚' }
  ];
  
  return (
    <div style={{ padding: '2rem' }}>
      <h2>Products</h2>
      <div style={{ 
        display: 'grid', 
        gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', 
        gap: '1rem' 
      }}>
        {products.map(product => (
          <div key={product.id} style={{
            border: '1px solid #ddd',
            borderRadius: '8px',
            padding: '1rem',
            textAlign: 'center'
          }}>
            <div style={{ fontSize: '3rem', marginBottom: '1rem' }}>
              {product.image}
            </div>
            <h3>{product.name}</h3>
            <p>₹{product.price.toLocaleString()}</p>
            <button 
              onClick={() => addItem(product)}
              style={{
                backgroundColor: '#007bff',
                color: 'white',
                border: 'none',
                padding: '0.5rem 1rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Add to Cart
            </button>
          </div>
        ))}
      </div>
    </div>
  );
}

function CartSummary() {
  const { 
    items, 
    itemCount, 
    subtotal, 
    discount, 
    total, 
    coupon,
    shipping,
    updateQuantity, 
    removeItem, 
    clearCart,
    applyCoupon,
    removeCoupon,
    setShipping
  } = useShoppingCart();
  
  const [couponCode, setCouponCode] = useState('');
  
  const availableCoupons = {
    'SAVE10': { code: 'SAVE10', discount: 10, description: '10% off' },
    'SAVE20': { code: 'SAVE20', discount: 20, description: '20% off' }
  };
  
  const shippingOptions = [
    { method: 'standard', cost: 0, description: 'Standard (Free)' },
    { method: 'express', cost: 200, description: 'Express (₹200)' },
    { method: 'overnight', cost: 500, description: 'Overnight (₹500)' }
  ];
  
  const handleApplyCoupon = () => {
    const coupon = availableCoupons[couponCode.toUpperCase()];
    if (coupon) {
      applyCoupon(coupon);
      setCouponCode('');
    } else {
      alert('Invalid coupon code');
    }
  };
  
  if (items.length === 0) {
    return (
      <div style={{ padding: '2rem', textAlign: 'center' }}>
        <h2>Your cart is empty</h2>
        <p>Add some products to get started!</p>
      </div>
    );
  }
  
  return (
    <div style={{ padding: '2rem' }}>
      <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '2rem' }}>
        <h2>Shopping Cart ({itemCount} items)</h2>
        <button 
          onClick={clearCart}
          style={{
            backgroundColor: '#dc3545',
            color: 'white',
            border: 'none',
            padding: '0.5rem 1rem',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Clear Cart
        </button>
      </div>
      
      {/* Cart Items */}
      <div style={{ marginBottom: '2rem' }}>
        {items.map(item => (
          <div key={item.id} style={{
            display: 'flex',
            justifyContent: 'space-between',
            alignItems: 'center',
            padding: '1rem',
            border: '1px solid #ddd',
            borderRadius: '8px',
            marginBottom: '1rem'
          }}>
            <div>
              <h4>{item.name}</h4>
              <p>₹{item.price.toLocaleString()} each</p>
            </div>
            
            <div style={{ display: 'flex', alignItems: 'center', gap: '1rem' }}>
              <div style={{ display: 'flex', alignItems: 'center', gap: '0.5rem' }}>
                <button 
                  onClick={() => updateQuantity(item.id, item.quantity - 1)}
                  style={{
                    backgroundColor: '#6c757d',
                    color: 'white',
                    border: 'none',
                    padding: '0.25rem 0.5rem',
                    borderRadius: '4px',
                    cursor: 'pointer'
                  }}
                >
                  -
                </button>
                <span>{item.quantity}</span>
                <button 
                  onClick={() => updateQuantity(item.id, item.quantity + 1)}
                  style={{
                    backgroundColor: '#6c757d',
                    color: 'white',
                    border: 'none',
                    padding: '0.25rem 0.5rem',
                    borderRadius: '4px',
                    cursor: 'pointer'
                  }}
                >
                  +
                </button>
              </div>
              
              <div>
                <strong>₹{(item.price * item.quantity).toLocaleString()}</strong>
              </div>
              
              <button 
                onClick={() => removeItem(item.id)}
                style={{
                  backgroundColor: '#dc3545',
                  color: 'white',
                  border: 'none',
                  padding: '0.25rem 0.5rem',
                  borderRadius: '4px',
                  cursor: 'pointer'
                }}
              >
                Remove
              </button>
            </div>
          </div>
        ))}
      </div>
      
      {/* Coupon Section */}
      <div style={{
        border: '1px solid #ddd',
        borderRadius: '8px',
        padding: '1rem',
        marginBottom: '2rem'
      }}>
        <h3>Coupon Code</h3>
        {coupon ? (
          <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
            <span>Applied: {coupon.code} ({coupon.description})</span>
            <button 
              onClick={removeCoupon}
              style={{
                backgroundColor: '#dc3545',
                color: 'white',
                border: 'none',
                padding: '0.25rem 0.5rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Remove
            </button>
          </div>
        ) : (
          <div style={{ display: 'flex', gap: '1rem' }}>
            <input
              type="text"
              value={couponCode}
              onChange={(e) => setCouponCode(e.target.value)}
              placeholder="Enter coupon code (try SAVE10 or SAVE20)"
              style={{
                flex: 1,
                padding: '0.5rem',
                border: '1px solid #ddd',
                borderRadius: '4px'
              }}
            />
            <button 
              onClick={handleApplyCoupon}
              style={{
                backgroundColor: '#28a745',
                color: 'white',
                border: 'none',
                padding: '0.5rem 1rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Apply
            </button>
          </div>
        )}
      </div>
      
      {/* Shipping Options */}
      <div style={{
        border: '1px solid #ddd',
        borderRadius: '8px',
        padding: '1rem',
        marginBottom: '2rem'
      }}>
        <h3>Shipping Options</h3>
        {shippingOptions.map(option => (
          <label key={option.method} style={{ display: 'block', marginBottom: '0.5rem' }}>
            <input
              type="radio"
              name="shipping"
              value={option.method}
              checked={shipping.method === option.method}
              onChange={() => setShipping(option)}
              style={{ marginRight: '0.5rem' }}
            />
            {option.description}
          </label>
        ))}
      </div>
      
      {/* Order Summary */}
      <div style={{
        border: '2px solid #007bff',
        borderRadius: '8px',
        padding: '1rem',
        backgroundColor: '#f8f9fa'
      }}>
        <h3>Order Summary</h3>
        <div style={{ display: 'flex', justifyContent: 'space-between', marginBottom: '0.5rem' }}>
          <span>Subtotal:</span>
          <span>₹{subtotal.toLocaleString()}</span>
        </div>
        {discount > 0 && (
          <div style={{ display: 'flex', justifyContent: 'space-between', marginBottom: '0.5rem', color: '#28a745' }}>
            <span>Discount:</span>
            <span>-₹{discount.toLocaleString()}</span>
          </div>
        )}
        <div style={{ display: 'flex', justifyContent: 'space-between', marginBottom: '0.5rem' }}>
          <span>Shipping:</span>
          <span>{shipping.cost === 0 ? 'Free' : `₹${shipping.cost.toLocaleString()}`}</span>
        </div>
        <hr />
        <div style={{ display: 'flex', justifyContent: 'space-between', fontSize: '1.2rem', fontWeight: 'bold' }}>
          <span>Total:</span>
          <span>₹{total.toLocaleString()}</span>
        </div>
        
        <button 
          style={{
            width: '100%',
            backgroundColor: '#007bff',
            color: 'white',
            border: 'none',
            padding: '1rem',
            borderRadius: '4px',
            cursor: 'pointer',
            fontSize: '1.1rem',
            fontWeight: 'bold',
            marginTop: '1rem'
          }}
        >
          Proceed to Checkout
        </button>
      </div>
    </div>
  );
}

// Main E-commerce App
function AdvancedContextApp() {
  const [currentView, setCurrentView] = useState('products');
  
  return (
    <ShoppingCartProvider>
      <div>
        <nav style={{
          backgroundColor: '#007bff',
          color: 'white',
          padding: '1rem 2rem',
          display: 'flex',
          justifyContent: 'space-between',
          alignItems: 'center'
        }}>
          <h1>E-Commerce Store</h1>
          <div style={{ display: 'flex', gap: '1rem' }}>
            <button 
              onClick={() => setCurrentView('products')}
              style={{
                backgroundColor: currentView === 'products' ? 'white' : 'transparent',
                color: currentView === 'products' ? '#007bff' : 'white',
                border: '1px solid white',
                padding: '0.5rem 1rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Products
            </button>
            <button 
              onClick={() => setCurrentView('cart')}
              style={{
                backgroundColor: currentView === 'cart' ? 'white' : 'transparent',
                color: currentView === 'cart' ? '#007bff' : 'white',
                border: '1px solid white',
                padding: '0.5rem 1rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Cart
            </button>
          </div>
        </nav>
        
        {currentView === 'products' ? <ProductList /> : <CartSummary />}
      </div>
    </ShoppingCartProvider>
  );
}
```

**Example 2: Multiple Contexts and Context Composition**
```jsx
// Multiple contexts working together
const NotificationContext = createContext();
const SettingsContext = createContext();
const AnalyticsContext = createContext();

// Notification Provider
function NotificationProvider({ children }) {
  const [notifications, setNotifications] = useState([]);
  
  const addNotification = (notification) => {
    const id = Date.now();
    const newNotification = {
      id,
      timestamp: new Date(),
      ...notification
    };
    
    setNotifications(prev => [...prev, newNotification]);
    
    // Auto remove after 5 seconds
    setTimeout(() => {
      removeNotification(id);
    }, 5000);
  };
  
  const removeNotification = (id) => {
    setNotifications(prev => prev.filter(n => n.id !== id));
  };
  
  const clearAllNotifications = () => {
    setNotifications([]);
  };
  
  const value = {
    notifications,
    addNotification,
    removeNotification,
    clearAllNotifications
  };
  
  return (
    <NotificationContext.Provider value={value}>
      {children}
    </NotificationContext.Provider>
  );
}

// Settings Provider
function SettingsProvider({ children }) {
  const [settings, setSettings] = useState({
    language: 'en',
    timezone: 'UTC',
    emailNotifications: true,
    pushNotifications: false,
    autoSave: true,
    theme: 'system' // light, dark, system
  });
  
  const updateSetting = (key, value) => {
    setSettings(prev => ({
      ...prev,
      [key]: value
    }));
  };
  
  const resetSettings = () => {
    setSettings({
      language: 'en',
      timezone: 'UTC',
      emailNotifications: true,
      pushNotifications: false,
      autoSave: true,
      theme: 'system'
    });
  };
  
  const value = {
    settings,
    updateSetting,
    resetSettings
  };
  
  return (
    <SettingsContext.Provider value={value}>
      {children}
    </SettingsContext.Provider>
  );
}

// Analytics Provider
function AnalyticsProvider({ children }) {
  const [events, setEvents] = useState([]);
  
  const trackEvent = (eventName, properties = {}) => {
    const event = {
      id: Date.now(),
      name: eventName,
      properties,
      timestamp: new Date(),
      sessionId: 'session_123' // In real app, this would be dynamic
    };
    
    setEvents(prev => [...prev, event]);
    
    // In real app, you'd send this to analytics service
    console.log('Analytics Event:', event);
  };
  
  const getEventsByName = (eventName) => {
    return events.filter(event => event.name === eventName);
  };
  
  const getEventsInTimeRange = (startDate, endDate) => {
    return events.filter(event => 
      event.timestamp >= startDate && event.timestamp <= endDate
    );
  };
  
  const value = {
    events,
    trackEvent,
    getEventsByName,
    getEventsInTimeRange
  };
  
  return (
    <AnalyticsContext.Provider value={value}>
      {children}
    </AnalyticsContext.Provider>
  );
}

// Custom hooks
function useNotifications() {
  const context = useContext(NotificationContext);
  if (!context) {
    throw new Error('useNotifications must be used within a NotificationProvider');
  }
  return context;
}

function useSettings() {
  const context = useContext(SettingsContext);
  if (!context) {
    throw new Error('useSettings must be used within a SettingsProvider');
  }
  return context;
}

function useAnalytics() {
  const context = useContext(AnalyticsContext);
  if (!context) {
    throw new Error('useAnalytics must be used within a AnalyticsProvider');
  }
  return context;
}

// Composite Provider for better organization
function AppProviders({ children }) {
  return (
    <SettingsProvider>
      <NotificationProvider>
        <AnalyticsProvider>
          {children}
        </AnalyticsProvider>
      </NotificationProvider>
    </SettingsProvider>
  );
}

// Components using multiple contexts
function NotificationCenter() {
  const { notifications, removeNotification, clearAllNotifications } = useNotifications();
  const { trackEvent } = useAnalytics();
  
  useEffect(() => {
    if (notifications.length > 0) {
      trackEvent('notifications_viewed', { count: notifications.length });
    }
  }, [notifications.length, trackEvent]);
  
  if (notifications.length === 0) {
    return (
      <div style={{ padding: '1rem', textAlign: 'center', color: '#666' }}>
        No notifications
      </div>
    );
  }
  
  return (
    <div style={{ maxWidth: '400px', margin: '1rem auto' }}>
      <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '1rem' }}>
        <h3>Notifications ({notifications.length})</h3>
        <button 
          onClick={() => {
            clearAllNotifications();
            trackEvent('notifications_cleared');
          }}
          style={{
            backgroundColor: '#dc3545',
            color: 'white',
            border: 'none',
            padding: '0.25rem 0.5rem',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Clear All
        </button>
      </div>
      
      {notifications.map(notification => (
        <div
          key={notification.id}
          style={{
            backgroundColor: notification.type === 'error' ? '#f8d7da' : 
                           notification.type === 'warning' ? '#fff3cd' : 
                           notification.type === 'success' ? '#d1edff' : '#e2e3e5',
            border: `1px solid ${notification.type === 'error' ? '#f5c6cb' : 
                                notification.type === 'warning' ? '#ffeaa7' : 
                                notification.type === 'success' ? '#bee5eb' : '#d6d8db'}`,
            borderRadius: '4px',
            padding: '1rem',
            marginBottom: '0.5rem',
            position: 'relative'
          }}
        >
          <button
            onClick={() => {
              removeNotification(notification.id);
              trackEvent('notification_dismissed', { type: notification.type });
            }}
            style={{
              position: 'absolute',
              top: '0.5rem',
              right: '0.5rem',
              background: 'none',
              border: 'none',
              fontSize: '1.2rem',
              cursor: 'pointer'
            }}
          >
            ×
          </button>
          
          <div style={{ marginRight: '2rem' }}>
            <strong>{notification.title}</strong>
            <p style={{ margin: '0.5rem 0 0 0' }}>{notification.message}</p>
            <small style={{ color: '#666' }}>
              {notification.timestamp.toLocaleTimeString()}
            </small>
          </div>
        </div>
      ))}
    </div>
  );
}

function SettingsPanel() {
  const { settings, updateSetting, resetSettings } = useSettings();
  const { addNotification } = useNotifications();
  const { trackEvent } = useAnalytics();
  
  const handleSettingChange = (key, value) => {
    updateSetting(key, value);
    addNotification({
      type: 'success',
      title: 'Setting Updated',
      message: `${key} has been updated to ${value}`
    });
    trackEvent('setting_changed', { setting: key, value });
  };
  
  return (
    <div style={{ maxWidth: '600px', margin: '2rem auto', padding: '2rem', border: '1px solid #ddd', borderRadius: '8px' }}>
      <h2>Settings</h2>
      
      <div style={{ marginBottom: '2rem' }}>
        <h3>Appearance</h3>
        <div style={{ marginBottom: '1rem' }}>
          <label style={{ display: 'block', marginBottom: '0.5rem' }}>Theme:</label>
          <select 
            value={settings.theme} 
            onChange={(e) => handleSettingChange('theme', e.target.value)}
            style={{ padding: '0.5rem', borderRadius: '4px', border: '1px solid #ddd' }}
          >
            <option value="light">Light</option>
            <option value="dark">Dark</option>
            <option value="system">System</option>
          </select>
        </div>
        
        <div style={{ marginBottom: '1rem' }}>
          <label style={{ display: 'block', marginBottom: '0.5rem' }}>Language:</label>
          <select 
            value={settings.language} 
            onChange={(e) => handleSettingChange('language', e.target.value)}
            style={{ padding: '0.5rem', borderRadius: '4px', border: '1px solid #ddd' }}
          >
            <option value="en">English</option>
            <option value="es">Spanish</option>
            <option value="fr">French</option>
            <option value="hi">Hindi</option>
          </select>
        </div>
      </div>
      
      <div style={{ marginBottom: '2rem' }}>
        <h3>Notifications</h3>
        <div style={{ marginBottom: '1rem' }}>
          <label>
            <input
              type="checkbox"
              checked={settings.emailNotifications}
              onChange={(e) => handleSettingChange('emailNotifications', e.target.checked)}
              style={{ marginRight: '0.5rem' }}
            />
            Email Notifications
          </label>
        </div>
        
        <div style={{ marginBottom: '1rem' }}>
          <label>
            <input
              type="checkbox"
              checked={settings.pushNotifications}
              onChange={(e) => handleSettingChange('pushNotifications', e.target.checked)}
              style={{ marginRight: '0.5rem' }}
            />
            Push Notifications
          </label>
        </div>
      </div>
      
      <div style={{ marginBottom: '2rem' }}>
        <h3>General</h3>
        <div style={{ marginBottom: '1rem' }}>
          <label>
            <input
              type="checkbox"
              checked={settings.autoSave}
              onChange={(e) => handleSettingChange('autoSave', e.target.checked)}
              style={{ marginRight: '0.5rem' }}
            />
            Auto Save
          </label>
        </div>
        
        <div style={{ marginBottom: '1rem' }}>
          <label style={{ display: 'block', marginBottom: '0.5rem' }}>Timezone:</label>
          <select 
            value={settings.timezone} 
            onChange={(e) => handleSettingChange('timezone', e.target.value)}
            style={{ padding: '0.5rem', borderRadius: '4px', border: '1px solid #ddd' }}
          >
            <option value="UTC">UTC</option>
            <option value="EST">Eastern Time</option>
            <option value="PST">Pacific Time</option>
            <option value="IST">India Standard Time</option>
          </select>
        </div>
      </div>
      
      <button 
        onClick={() => {
          resetSettings();
          addNotification({
            type: 'info',
            title: 'Settings Reset',
            message: 'All settings have been reset to default values'
          });
          trackEvent('settings_reset');
        }}
        style={{
          backgroundColor: '#6c757d',
          color: 'white',
          border: 'none',
          padding: '0.75rem 1.5rem',
          borderRadius: '4px',
          cursor: 'pointer'
        }}
      >
        Reset to Defaults
      </button>
    </div>
  );
}

function AnalyticsDashboard() {
  const { events, getEventsByName } = useAnalytics();
  const { addNotification } = useNotifications();
  
  const eventCounts = events.reduce((acc, event) => {
    acc[event.name] = (acc[event.name] || 0) + 1;
    return acc;
  }, {});
  
  return (
    <div style={{ maxWidth: '800px', margin: '2rem auto', padding: '2rem', border: '1px solid #ddd', borderRadius: '8px' }}>
      <h2>Analytics Dashboard</h2>
      
      <div style={{ marginBottom: '2rem' }}>
        <h3>Event Summary</h3>
        <p>Total Events: {events.length}</p>
        
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', gap: '1rem' }}>
          {Object.entries(eventCounts).map(([eventName, count]) => (
            <div key={eventName} style={{
              backgroundColor: '#f8f9fa',
              padding: '1rem',
              borderRadius: '8px',
              border: '1px solid #dee2e6'
            }}>
              <h4>{eventName.replace(/_/g, ' ').toUpperCase()}</h4>
              <p style={{ fontSize: '2rem', fontWeight: 'bold', margin: '0.5rem 0' }}>{count}</p>
            </div>
          ))}
        </div>
      </div>
      
      <div>
        <h3>Recent Events</h3>
        <div style={{ maxHeight: '300px', overflowY: 'auto' }}>
          {events.slice(-10).reverse().map(event => (
            <div key={event.id} style={{
              backgroundColor: '#f8f9fa',
              padding: '1rem',
              marginBottom: '0.5rem',
              borderRadius: '4px',
              border: '1px solid #dee2e6'
            }}>
              <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
                <strong>{event.name}</strong>
                <small>{event.timestamp.toLocaleString()}</small>
              </div>
              {Object.keys(event.properties).length > 0 && (
                <div style={{ marginTop: '0.5rem', fontSize: '0.9rem', color: '#666' }}>
                  Properties: {JSON.stringify(event.properties)}
                </div>
              )}
            </div>
          ))}
        </div>
      </div>
      
      <button 
        onClick={() => {
          addNotification({
            type: 'info',
            title: 'Analytics',
            message: `You have ${events.length} total events tracked`
          });
        }}
        style={{
          backgroundColor: '#007bff',
          color: 'white',
          border: 'none',
          padding: '0.75rem 1.5rem',
          borderRadius: '4px',
          cursor: 'pointer',
          marginTop: '1rem'
        }}
      >
        Show Summary Notification
      </button>
    </div>
  );
}

// Main app with multiple contexts
function MultiContextApp() {
  const [currentView, setCurrentView] = useState('settings');
  
  return (
    <AppProviders>
      <div>
        <nav style={{
          backgroundColor: '#343a40',
          color: 'white',
          padding: '1rem 2rem',
          display: 'flex',
          justifyContent: 'space-between',
          alignItems: 'center'
        }}>
          <h1>Multi-Context App</h1>
          <div style={{ display: 'flex', gap: '1rem' }}>
            {['settings', 'notifications', 'analytics'].map(view => (
              <button
                key={view}
                onClick={() => setCurrentView(view)}
                style={{
                  backgroundColor: currentView === view ? 'white' : 'transparent',
                  color: currentView === view ? '#343a40' : 'white',
                  border: '1px solid white',
                  padding: '0.5rem 1rem',
                  borderRadius: '4px',
                  cursor: 'pointer',
                  textTransform: 'capitalize'
                }}
              >
                {view}
              </button>
            ))}
          </div>
        </nav>
        
        {currentView === 'settings' && <SettingsPanel />}
        {currentView === 'notifications' && <NotificationCenter />}
        {currentView === 'analytics' && <AnalyticsDashboard />}
      </div>
    </AppProviders>
  );
}
```

**Context Best Practices and Patterns:**
```jsx
// 1. Context with error boundaries
class ContextErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }
  
  static getDerivedStateFromError(error) {
    return { hasError: true };
  }
  
  componentDidCatch(error, errorInfo) {
    console.error('Context Error:', error, errorInfo);
  }
  
  render() {
    if (this.state.hasError) {
      return <div>Something went wrong with the context.</div>;
    }
    
    return this.props.children;
  }
}

// 2. Context with local storage persistence
function usePersistentContext(key, initialValue) {
  const [value, setValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error('Error reading from localStorage:', error);
      return initialValue;
    }
  });
  
  const setPersistentValue = (newValue) => {
    try {
      setValue(newValue);
      window.localStorage.setItem(key, JSON.stringify(newValue));
    } catch (error) {
      console.error('Error writing to localStorage:', error);
    }
  };
  
  return [value, setPersistentValue];
}

// 3. Context performance optimization
const ExpensiveContext = createContext();

function ExpensiveProvider({ children }) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(false);
  
  // Memoize the context value to prevent unnecessary re-renders
  const value = useMemo(() => ({
    data,
    loading,
    setData,
    setLoading
  }), [data, loading]);
  
  return (
    <ExpensiveContext.Provider value={value}>
      {children}
    </ExpensiveContext.Provider>
  );
}
```

**Interview Questions:**
1. What is the Context API and when should you use it?
2. What problem does Context API solve?
3. How do you create and use a Context in React?
4. What is the difference between Context API and prop drilling?
5. How do you optimize Context performance?
6. Can you use multiple contexts in a single component?
7. What are the limitations of Context API?
8. How do you handle context errors and provide fallbacks?
9. When should you use Context API vs external state management libraries?
10. How do you test components that use Context?

---#
## 🔹 Day 23–25: Redux - DEEP DIVE

**Definition (English):**
Redux is a predictable state container for JavaScript applications, commonly used with React for managing application state. It follows three core principles: single source of truth (one store), state is read-only (immutable), and changes are made with pure functions (reducers). Redux provides a centralized way to manage state with a unidirectional data flow pattern, making state changes predictable and debuggable.

**Hinglish Deep Explanation:**
Redux ek powerful state management library hai jo large applications ke liye use hoti hai. Ye teen main principles follow karti hai: ek hi store mein saara state, state ko directly change nahi kar sakte (immutable), aur changes sirf pure functions (reducers) se hoti hain. Redux mein data flow ek direction mein hota hai - Action dispatch karte hain, Reducer state update karta hai, aur Store components ko notify karta hai.

**Redux Deep Understanding:**

**1. Redux Core Concepts and Setup:**
```jsx
// 1. Actions - Plain objects describing what happened
const ActionTypes = {
  // User actions
  LOGIN_REQUEST: 'LOGIN_REQUEST',
  LOGIN_SUCCESS: 'LOGIN_SUCCESS',
  LOGIN_FAILURE: 'LOGIN_FAILURE',
  LOGOUT: 'LOGOUT',
  UPDATE_PROFILE: 'UPDATE_PROFILE',
  
  // Todo actions
  ADD_TODO: 'ADD_TODO',
  TOGGLE_TODO: 'TOGGLE_TODO',
  DELETE_TODO: 'DELETE_TODO',
  EDIT_TODO: 'EDIT_TODO',
  SET_FILTER: 'SET_FILTER',
  CLEAR_COMPLETED: 'CLEAR_COMPLETED',
  
  // UI actions
  SET_LOADING: 'SET_LOADING',
  SET_ERROR: 'SET_ERROR',
  CLEAR_ERROR: 'CLEAR_ERROR',
  TOGGLE_SIDEBAR: 'TOGGLE_SIDEBAR'
};

// Action Creators - Functions that return actions
const userActions = {
  loginRequest: () => ({
    type: ActionTypes.LOGIN_REQUEST
  }),
  
  loginSuccess: (user) => ({
    type: ActionTypes.LOGIN_SUCCESS,
    payload: user
  }),
  
  loginFailure: (error) => ({
    type: ActionTypes.LOGIN_FAILURE,
    payload: error
  }),
  
  logout: () => ({
    type: ActionTypes.LOGOUT
  }),
  
  updateProfile: (updates) => ({
    type: ActionTypes.UPDATE_PROFILE,
    payload: updates
  })
};

const todoActions = {
  addTodo: (text) => ({
    type: ActionTypes.ADD_TODO,
    payload: {
      id: Date.now(),
      text,
      completed: false,
      createdAt: new Date().toISOString()
    }
  }),
  
  toggleTodo: (id) => ({
    type: ActionTypes.TOGGLE_TODO,
    payload: id
  }),
  
  deleteTodo: (id) => ({
    type: ActionTypes.DELETE_TODO,
    payload: id
  }),
  
  editTodo: (id, text) => ({
    type: ActionTypes.EDIT_TODO,
    payload: { id, text }
  }),
  
  setFilter: (filter) => ({
    type: ActionTypes.SET_FILTER,
    payload: filter
  }),
  
  clearCompleted: () => ({
    type: ActionTypes.CLEAR_COMPLETED
  })
};

const uiActions = {
  setLoading: (loading) => ({
    type: ActionTypes.SET_LOADING,
    payload: loading
  }),
  
  setError: (error) => ({
    type: ActionTypes.SET_ERROR,
    payload: error
  }),
  
  clearError: () => ({
    type: ActionTypes.CLEAR_ERROR
  }),
  
  toggleSidebar: () => ({
    type: ActionTypes.TOGGLE_SIDEBAR
  })
};

// 2. Reducers - Pure functions that specify how state changes
const initialUserState = {
  currentUser: null,
  isAuthenticated: false,
  loading: false,
  error: null
};

function userReducer(state = initialUserState, action) {
  switch (action.type) {
    case ActionTypes.LOGIN_REQUEST:
      return {
        ...state,
        loading: true,
        error: null
      };
    
    case ActionTypes.LOGIN_SUCCESS:
      return {
        ...state,
        currentUser: action.payload,
        isAuthenticated: true,
        loading: false,
        error: null
      };
    
    case ActionTypes.LOGIN_FAILURE:
      return {
        ...state,
        currentUser: null,
        isAuthenticated: false,
        loading: false,
        error: action.payload
      };
    
    case ActionTypes.LOGOUT:
      return {
        ...state,
        currentUser: null,
        isAuthenticated: false,
        error: null
      };
    
    case ActionTypes.UPDATE_PROFILE:
      return {
        ...state,
        currentUser: {
          ...state.currentUser,
          ...action.payload
        }
      };
    
    default:
      return state;
  }
}

const initialTodoState = {
  items: [],
  filter: 'ALL', // ALL, ACTIVE, COMPLETED
  lastId: 0
};

function todoReducer(state = initialTodoState, action) {
  switch (action.type) {
    case ActionTypes.ADD_TODO:
      return {
        ...state,
        items: [...state.items, action.payload],
        lastId: action.payload.id
      };
    
    case ActionTypes.TOGGLE_TODO:
      return {
        ...state,
        items: state.items.map(todo =>
          todo.id === action.payload
            ? { ...todo, completed: !todo.completed }
            : todo
        )
      };
    
    case ActionTypes.DELETE_TODO:
      return {
        ...state,
        items: state.items.filter(todo => todo.id !== action.payload)
      };
    
    case ActionTypes.EDIT_TODO:
      return {
        ...state,
        items: state.items.map(todo =>
          todo.id === action.payload.id
            ? { ...todo, text: action.payload.text }
            : todo
        )
      };
    
    case ActionTypes.SET_FILTER:
      return {
        ...state,
        filter: action.payload
      };
    
    case ActionTypes.CLEAR_COMPLETED:
      return {
        ...state,
        items: state.items.filter(todo => !todo.completed)
      };
    
    default:
      return state;
  }
}

const initialUIState = {
  loading: false,
  error: null,
  sidebarOpen: false,
  theme: 'light'
};

function uiReducer(state = initialUIState, action) {
  switch (action.type) {
    case ActionTypes.SET_LOADING:
      return {
        ...state,
        loading: action.payload
      };
    
    case ActionTypes.SET_ERROR:
      return {
        ...state,
        error: action.payload
      };
    
    case ActionTypes.CLEAR_ERROR:
      return {
        ...state,
        error: null
      };
    
    case ActionTypes.TOGGLE_SIDEBAR:
      return {
        ...state,
        sidebarOpen: !state.sidebarOpen
      };
    
    default:
      return state;
  }
}

// 3. Root Reducer - Combines all reducers
import { combineReducers } from 'redux';

const rootReducer = combineReducers({
  user: userReducer,
  todos: todoReducer,
  ui: uiReducer
});

// 4. Store - Holds the complete state tree
import { createStore, applyMiddleware, compose } from 'redux';
import { thunk } from 'redux-thunk';

// Redux DevTools Extension
const composeEnhancers = 
  (typeof window !== 'undefined' && window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__) || compose;

const store = createStore(
  rootReducer,
  composeEnhancers(
    applyMiddleware(thunk)
  )
);

// 5. React-Redux Integration
import React from 'react';
import { Provider, useSelector, useDispatch } from 'react-redux';

// Selectors - Functions to extract specific pieces of state
const userSelectors = {
  getCurrentUser: (state) => state.user.currentUser,
  isAuthenticated: (state) => state.user.isAuthenticated,
  isLoading: (state) => state.user.loading,
  getError: (state) => state.user.error
};

const todoSelectors = {
  getAllTodos: (state) => state.todos.items,
  getTodosByFilter: (state) => {
    const { items, filter } = state.todos;
    switch (filter) {
      case 'ACTIVE':
        return items.filter(todo => !todo.completed);
      case 'COMPLETED':
        return items.filter(todo => todo.completed);
      default:
        return items;
    }
  },
  getCurrentFilter: (state) => state.todos.filter,
  getTodoCount: (state) => state.todos.items.length,
  getCompletedCount: (state) => state.todos.items.filter(todo => todo.completed).length,
  getActiveCount: (state) => state.todos.items.filter(todo => !todo.completed).length
};

const uiSelectors = {
  isLoading: (state) => state.ui.loading,
  getError: (state) => state.ui.error,
  isSidebarOpen: (state) => state.ui.sidebarOpen,
  getTheme: (state) => state.ui.theme
};

// Components using Redux
function LoginForm() {
  const dispatch = useDispatch();
  const { isLoading, error } = useSelector(state => ({
    isLoading: userSelectors.isLoading(state),
    error: userSelectors.getError(state)
  }));
  
  const [credentials, setCredentials] = useState({
    email: '',
    password: ''
  });
  
  const handleSubmit = async (e) => {
    e.preventDefault();
    
    dispatch(userActions.loginRequest());
    
    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 1000));
      
      if (credentials.email === 'admin@example.com') {
        dispatch(userActions.loginSuccess({
          id: 1,
          name: 'Admin User',
          email: credentials.email,
          role: 'admin'
        }));
      } else if (credentials.email === 'user@example.com') {
        dispatch(userActions.loginSuccess({
          id: 2,
          name: 'Regular User',
          email: credentials.email,
          role: 'user'
        }));
      } else {
        throw new Error('Invalid credentials');
      }
    } catch (error) {
      dispatch(userActions.loginFailure(error.message));
    }
  };
  
  return (
    <form onSubmit={handleSubmit} style={{ maxWidth: '400px', margin: '2rem auto', padding: '2rem', border: '1px solid #ddd', borderRadius: '8px' }}>
      <h2>Login</h2>
      
      {error && (
        <div style={{ backgroundColor: '#f8d7da', color: '#721c24', padding: '0.5rem', borderRadius: '4px', marginBottom: '1rem' }}>
          {error}
        </div>
      )}
      
      <div style={{ marginBottom: '1rem' }}>
        <input
          type="email"
          placeholder="Email (try admin@example.com or user@example.com)"
          value={credentials.email}
          onChange={(e) => setCredentials(prev => ({ ...prev, email: e.target.value }))}
          style={{ width: '100%', padding: '0.5rem', border: '1px solid #ddd', borderRadius: '4px' }}
          required
        />
      </div>
      
      <div style={{ marginBottom: '1rem' }}>
        <input
          type="password"
          placeholder="Password"
          value={credentials.password}
          onChange={(e) => setCredentials(prev => ({ ...prev, password: e.target.value }))}
          style={{ width: '100%', padding: '0.5rem', border: '1px solid #ddd', borderRadius: '4px' }}
          required
        />
      </div>
      
      <button 
        type="submit" 
        disabled={isLoading}
        style={{
          width: '100%',
          padding: '0.75rem',
          backgroundColor: '#007bff',
          color: 'white',
          border: 'none',
          borderRadius: '4px',
          cursor: isLoading ? 'not-allowed' : 'pointer',
          opacity: isLoading ? 0.6 : 1
        }}
      >
        {isLoading ? 'Logging in...' : 'Login'}
      </button>
    </form>
  );
}

function TodoApp() {
  const dispatch = useDispatch();
  const {
    todos,
    filter,
    todoCount,
    completedCount,
    activeCount
  } = useSelector(state => ({
    todos: todoSelectors.getTodosByFilter(state),
    filter: todoSelectors.getCurrentFilter(state),
    todoCount: todoSelectors.getTodoCount(state),
    completedCount: todoSelectors.getCompletedCount(state),
    activeCount: todoSelectors.getActiveCount(state)
  }));
  
  const [newTodo, setNewTodo] = useState('');
  const [editingId, setEditingId] = useState(null);
  const [editText, setEditText] = useState('');
  
  const handleAddTodo = (e) => {
    e.preventDefault();
    if (newTodo.trim()) {
      dispatch(todoActions.addTodo(newTodo.trim()));
      setNewTodo('');
    }
  };
  
  const handleEditStart = (todo) => {
    setEditingId(todo.id);
    setEditText(todo.text);
  };
  
  const handleEditSave = () => {
    if (editText.trim()) {
      dispatch(todoActions.editTodo(editingId, editText.trim()));
    }
    setEditingId(null);
    setEditText('');
  };
  
  const handleEditCancel = () => {
    setEditingId(null);
    setEditText('');
  };
  
  return (
    <div style={{ maxWidth: '600px', margin: '2rem auto', padding: '2rem' }}>
      <h2>Todo App with Redux</h2>
      
      {/* Add Todo Form */}
      <form onSubmit={handleAddTodo} style={{ marginBottom: '2rem' }}>
        <div style={{ display: 'flex', gap: '1rem' }}>
          <input
            type="text"
            value={newTodo}
            onChange={(e) => setNewTodo(e.target.value)}
            placeholder="Add a new todo..."
            style={{ flex: 1, padding: '0.5rem', border: '1px solid #ddd', borderRadius: '4px' }}
          />
          <button 
            type="submit"
            style={{
              backgroundColor: '#28a745',
              color: 'white',
              border: 'none',
              padding: '0.5rem 1rem',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            Add
          </button>
        </div>
      </form>
      
      {/* Filter Buttons */}
      <div style={{ marginBottom: '2rem', display: 'flex', gap: '1rem', justifyContent: 'center' }}>
        {['ALL', 'ACTIVE', 'COMPLETED'].map(filterType => (
          <button
            key={filterType}
            onClick={() => dispatch(todoActions.setFilter(filterType))}
            style={{
              backgroundColor: filter === filterType ? '#007bff' : '#f8f9fa',
              color: filter === filterType ? 'white' : '#333',
              border: '1px solid #ddd',
              padding: '0.5rem 1rem',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            {filterType}
          </button>
        ))}
      </div>
      
      {/* Stats */}
      <div style={{ marginBottom: '2rem', textAlign: 'center', color: '#666' }}>
        Total: {todoCount} | Active: {activeCount} | Completed: {completedCount}
      </div>
      
      {/* Todo List */}
      <div>
        {todos.length === 0 ? (
          <p style={{ textAlign: 'center', color: '#666' }}>
            {filter === 'ALL' ? 'No todos yet' : `No ${filter.toLowerCase()} todos`}
          </p>
        ) : (
          todos.map(todo => (
            <div
              key={todo.id}
              style={{
                display: 'flex',
                alignItems: 'center',
                padding: '1rem',
                border: '1px solid #ddd',
                borderRadius: '4px',
                marginBottom: '0.5rem',
                backgroundColor: todo.completed ? '#f8f9fa' : 'white'
              }}
            >
              <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => dispatch(todoActions.toggleTodo(todo.id))}
                style={{ marginRight: '1rem' }}
              />
              
              {editingId === todo.id ? (
                <div style={{ flex: 1, display: 'flex', gap: '0.5rem' }}>
                  <input
                    type="text"
                    value={editText}
                    onChange={(e) => setEditText(e.target.value)}
                    onKeyPress={(e) => e.key === 'Enter' && handleEditSave()}
                    style={{ flex: 1, padding: '0.25rem', border: '1px solid #ddd', borderRadius: '4px' }}
                    autoFocus
                  />
                  <button 
                    onClick={handleEditSave}
                    style={{ backgroundColor: '#28a745', color: 'white', border: 'none', padding: '0.25rem 0.5rem', borderRadius: '4px', cursor: 'pointer' }}
                  >
                    Save
                  </button>
                  <button 
                    onClick={handleEditCancel}
                    style={{ backgroundColor: '#6c757d', color: 'white', border: 'none', padding: '0.25rem 0.5rem', borderRadius: '4px', cursor: 'pointer' }}
                  >
                    Cancel
                  </button>
                </div>
              ) : (
                <>
                  <span 
                    style={{ 
                      flex: 1, 
                      textDecoration: todo.completed ? 'line-through' : 'none',
                      color: todo.completed ? '#666' : '#333'
                    }}
                  >
                    {todo.text}
                  </span>
                  
                  <div style={{ display: 'flex', gap: '0.5rem' }}>
                    <button 
                      onClick={() => handleEditStart(todo)}
                      style={{ backgroundColor: '#ffc107', color: '#333', border: 'none', padding: '0.25rem 0.5rem', borderRadius: '4px', cursor: 'pointer' }}
                    >
                      Edit
                    </button>
                    <button 
                      onClick={() => dispatch(todoActions.deleteTodo(todo.id))}
                      style={{ backgroundColor: '#dc3545', color: 'white', border: 'none', padding: '0.25rem 0.5rem', borderRadius: '4px', cursor: 'pointer' }}
                    >
                      Delete
                    </button>
                  </div>
                </>
              )}
            </div>
          ))
        )}
      </div>
      
      {/* Clear Completed Button */}
      {completedCount > 0 && (
        <div style={{ textAlign: 'center', marginTop: '2rem' }}>
          <button 
            onClick={() => dispatch(todoActions.clearCompleted())}
            style={{
              backgroundColor: '#dc3545',
              color: 'white',
              border: 'none',
              padding: '0.5rem 1rem',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            Clear Completed ({completedCount})
          </button>
        </div>
      )}
    </div>
  );
}

function UserProfile() {
  const dispatch = useDispatch();
  const { user, isAuthenticated } = useSelector(state => ({
    user: userSelectors.getCurrentUser(state),
    isAuthenticated: userSelectors.isAuthenticated(state)
  }));
  
  const [editing, setEditing] = useState(false);
  const [profileData, setProfileData] = useState({
    name: '',
    email: ''
  });
  
  useEffect(() => {
    if (user) {
      setProfileData({
        name: user.name || '',
        email: user.email || ''
      });
    }
  }, [user]);
  
  const handleSave = () => {
    dispatch(userActions.updateProfile(profileData));
    setEditing(false);
  };
  
  const handleCancel = () => {
    setProfileData({
      name: user.name || '',
      email: user.email || ''
    });
    setEditing(false);
  };
  
  if (!isAuthenticated) {
    return <LoginForm />;
  }
  
  return (
    <div style={{ maxWidth: '500px', margin: '2rem auto', padding: '2rem', border: '1px solid #ddd', borderRadius: '8px' }}>
      <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '2rem' }}>
        <h2>User Profile</h2>
        <button 
          onClick={() => dispatch(userActions.logout())}
          style={{
            backgroundColor: '#dc3545',
            color: 'white',
            border: 'none',
            padding: '0.5rem 1rem',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Logout
        </button>
      </div>
      
      {editing ? (
        <div>
          <div style={{ marginBottom: '1rem' }}>
            <label style={{ display: 'block', marginBottom: '0.5rem' }}>Name:</label>
            <input
              type="text"
              value={profileData.name}
              onChange={(e) => setProfileData(prev => ({ ...prev, name: e.target.value }))}
              style={{ width: '100%', padding: '0.5rem', border: '1px solid #ddd', borderRadius: '4px' }}
            />
          </div>
          
          <div style={{ marginBottom: '2rem' }}>
            <label style={{ display: 'block', marginBottom: '0.5rem' }}>Email:</label>
            <input
              type="email"
              value={profileData.email}
              onChange={(e) => setProfileData(prev => ({ ...prev, email: e.target.value }))}
              style={{ width: '100%', padding: '0.5rem', border: '1px solid #ddd', borderRadius: '4px' }}
            />
          </div>
          
          <div style={{ display: 'flex', gap: '1rem' }}>
            <button 
              onClick={handleSave}
              style={{
                backgroundColor: '#28a745',
                color: 'white',
                border: 'none',
                padding: '0.5rem 1rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Save
            </button>
            <button 
              onClick={handleCancel}
              style={{
                backgroundColor: '#6c757d',
                color: 'white',
                border: 'none',
                padding: '0.5rem 1rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Cancel
            </button>
          </div>
        </div>
      ) : (
        <div>
          <div style={{ marginBottom: '1rem' }}>
            <strong>Name:</strong> {user.name}
          </div>
          <div style={{ marginBottom: '1rem' }}>
            <strong>Email:</strong> {user.email}
          </div>
          <div style={{ marginBottom: '2rem' }}>
            <strong>Role:</strong> {user.role}
          </div>
          
          <button 
            onClick={() => setEditing(true)}
            style={{
              backgroundColor: '#007bff',
              color: 'white',
              border: 'none',
              padding: '0.5rem 1rem',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            Edit Profile
          </button>
        </div>
      )}
    </div>
  );
}

// Main App Component
function BasicReduxApp() {
  const [currentView, setCurrentView] = useState('todos');
  const { isAuthenticated, sidebarOpen } = useSelector(state => ({
    isAuthenticated: userSelectors.isAuthenticated(state),
    sidebarOpen: uiSelectors.isSidebarOpen(state)
  }));
  
  return (
    <Provider store={store}>
      <div style={{ display: 'flex', minHeight: '100vh' }}>
        {/* Sidebar */}
        <aside style={{
          width: sidebarOpen ? '250px' : '60px',
          backgroundColor: '#343a40',
          color: 'white',
          transition: 'width 0.3s ease',
          overflow: 'hidden'
        }}>
          <div style={{ padding: '1rem' }}>
            <h3 style={{ whiteSpace: 'nowrap' }}>Redux App</h3>
          </div>
          
          <nav>
            {['todos', 'profile'].map(view => (
              <button
                key={view}
                onClick={() => setCurrentView(view)}
                style={{
                  width: '100%',
                  backgroundColor: currentView === view ? '#495057' : 'transparent',
                  color: 'white',
                  border: 'none',
                  padding: '1rem',
                  textAlign: 'left',
                  cursor: 'pointer',
                  textTransform: 'capitalize',
                  whiteSpace: 'nowrap'
                }}
              >
                {view}
              </button>
            ))}
          </nav>
        </aside>
        
        {/* Main Content */}
        <main style={{ flex: 1, backgroundColor: '#f8f9fa' }}>
          <header style={{
            backgroundColor: 'white',
            padding: '1rem 2rem',
            borderBottom: '1px solid #dee2e6',
            display: 'flex',
            justifyContent: 'space-between',
            alignItems: 'center'
          }}>
            <h1 style={{ textTransform: 'capitalize' }}>{currentView}</h1>
            {isAuthenticated && (
              <span>Welcome back!</span>
            )}
          </header>
          
          <div style={{ padding: '2rem' }}>
            {currentView === 'todos' && <TodoApp />}
            {currentView === 'profile' && <UserProfile />}
          </div>
        </main>
      </div>
    </Provider>
  );
}
```

**Example 1: Advanced Redux with Async Actions (Thunk)**
```jsx
// Advanced async action creators using Redux Thunk
const asyncUserActions = {
  // Async login with API call
  loginUser: (credentials) => {
    return async (dispatch, getState) => {
      dispatch(userActions.loginRequest());
      
      try {
        // Simulate API call with realistic delay
        const response = await fetch('/api/auth/login', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify(credentials)
        });
        
        if (!response.ok) {
          throw new Error('Login failed');
        }
        
        const userData = await response.json();
        
        // Store token in localStorage
        localStorage.setItem('authToken', userData.token);
        
        dispatch(userActions.loginSuccess(userData.user));
        
        // Redirect or perform additional actions
        return userData;
        
      } catch (error) {
        dispatch(userActions.loginFailure(error.message));
        throw error;
      }
    };
  },
  
  // Fetch user profile
  fetchUserProfile: (userId) => {
    return async (dispatch, getState) => {
      const { user } = getState();
      
      // Don't fetch if already loading
      if (user.loading) return;
      
      dispatch(uiActions.setLoading(true));
      
      try {
        const response = await fetch(`/api/users/${userId}`, {
          headers: {
            'Authorization': `Bearer ${localStorage.getItem('authToken')}`
          }
        });
        
        if (!response.ok) {
          throw new Error('Failed to fetch profile');
        }
        
        const profileData = await response.json();
        dispatch(userActions.updateProfile(profileData));
        
      } catch (error) {
        dispatch(uiActions.setError(error.message));
      } finally {
        dispatch(uiActions.setLoading(false));
      }
    };
  },
  
  // Auto-login from stored token
  autoLogin: () => {
    return async (dispatch) => {
      const token = localStorage.getItem('authToken');
      
      if (!token) return;
      
      dispatch(userActions.loginRequest());
      
      try {
        const response = await fetch('/api/auth/verify', {
          headers: {
            'Authorization': `Bearer ${token}`
          }
        });
        
        if (!response.ok) {
          localStorage.removeItem('authToken');
          throw new Error('Token invalid');
        }
        
        const userData = await response.json();
        dispatch(userActions.loginSuccess(userData));
        
      } catch (error) {
        dispatch(userActions.loginFailure(error.message));
      }
    };
  }
};

// Advanced todo actions with API integration
const asyncTodoActions = {
  // Fetch todos from server
  fetchTodos: () => {
    return async (dispatch, getState) => {
      dispatch(uiActions.setLoading(true));
      
      try {
        const response = await fetch('/api/todos', {
          headers: {
            'Authorization': `Bearer ${localStorage.getItem('authToken')}`
          }
        });
        
        if (!response.ok) {
          throw new Error('Failed to fetch todos');
        }
        
        const todos = await response.json();
        
        // Dispatch multiple actions to update state
        dispatch({ type: 'SET_TODOS', payload: todos });
        
      } catch (error) {
        dispatch(uiActions.setError(error.message));
      } finally {
        dispatch(uiActions.setLoading(false));
      }
    };
  },
  
  // Create todo on server
  createTodo: (todoText) => {
    return async (dispatch, getState) => {
      const tempId = Date.now();
      
      // Optimistic update
      dispatch(todoActions.addTodo(todoText));
      
      try {
        const response = await fetch('/api/todos', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'Authorization': `Bearer ${localStorage.getItem('authToken')}`
          },
          body: JSON.stringify({ text: todoText })
        });
        
        if (!response.ok) {
          // Revert optimistic update
          dispatch(todoActions.deleteTodo(tempId));
          throw new Error('Failed to create todo');
        }
        
        const createdTodo = await response.json();
        
        // Replace temp todo with server response
        dispatch({ type: 'REPLACE_TODO', payload: { tempId, todo: createdTodo } });
        
      } catch (error) {
        dispatch(uiActions.setError(error.message));
      }
    };
  },
  
  // Batch operations
  batchUpdateTodos: (updates) => {
    return async (dispatch, getState) => {
      dispatch(uiActions.setLoading(true));
      
      try {
        const response = await fetch('/api/todos/batch', {
          method: 'PATCH',
          headers: {
            'Content-Type': 'application/json',
            'Authorization': `Bearer ${localStorage.getItem('authToken')}`
          },
          body: JSON.stringify({ updates })
        });
        
        if (!response.ok) {
          throw new Error('Batch update failed');
        }
        
        const updatedTodos = await response.json();
        dispatch({ type: 'SET_TODOS', payload: updatedTodos });
        
      } catch (error) {
        dispatch(uiActions.setError(error.message));
      } finally {
        dispatch(uiActions.setLoading(false));
      }
    };
  }
};

// Component using async actions
function AdvancedTodoApp() {
  const dispatch = useDispatch();
  const {
    todos,
    loading,
    error,
    isAuthenticated
  } = useSelector(state => ({
    todos: todoSelectors.getAllTodos(state),
    loading: uiSelectors.isLoading(state),
    error: uiSelectors.getError(state),
    isAuthenticated: userSelectors.isAuthenticated(state)
  }));
  
  const [newTodo, setNewTodo] = useState('');
  const [selectedTodos, setSelectedTodos] = useState([]);
  
  // Auto-login on component mount
  useEffect(() => {
    dispatch(asyncUserActions.autoLogin());
  }, [dispatch]);
  
  // Fetch todos when authenticated
  useEffect(() => {
    if (isAuthenticated) {
      dispatch(asyncTodoActions.fetchTodos());
    }
  }, [isAuthenticated, dispatch]);
  
  const handleAddTodo = async (e) => {
    e.preventDefault();
    if (newTodo.trim()) {
      try {
        await dispatch(asyncTodoActions.createTodo(newTodo.trim()));
        setNewTodo('');
      } catch (error) {
        console.error('Failed to add todo:', error);
      }
    }
  };
  
  const handleBatchComplete = () => {
    const updates = selectedTodos.map(id => ({
      id,
      completed: true
    }));
    
    dispatch(asyncTodoActions.batchUpdateTodos(updates));
    setSelectedTodos([]);
  };
  
  const handleTodoSelect = (todoId) => {
    setSelectedTodos(prev => 
      prev.includes(todoId)
        ? prev.filter(id => id !== todoId)
        : [...prev, todoId]
    );
  };
  
  if (!isAuthenticated) {
    return <LoginForm />;
  }
  
  return (
    <div style={{ maxWidth: '800px', margin: '2rem auto', padding: '2rem' }}>
      <h2>Advanced Todo App with Redux</h2>
      
      {error && (
        <div style={{
          backgroundColor: '#f8d7da',
          color: '#721c24',
          padding: '1rem',
          borderRadius: '4px',
          marginBottom: '1rem'
        }}>
          Error: {error}
          <button 
            onClick={() => dispatch(uiActions.clearError())}
            style={{ float: 'right', background: 'none', border: 'none', fontSize: '1.2rem', cursor: 'pointer' }}
          >
            ×
          </button>
        </div>
      )}
      
      {loading && (
        <div style={{
          backgroundColor: '#d1ecf1',
          color: '#0c5460',
          padding: '1rem',
          borderRadius: '4px',
          marginBottom: '1rem',
          textAlign: 'center'
        }}>
          Loading...
        </div>
      )}
      
      {/* Add Todo Form */}
      <form onSubmit={handleAddTodo} style={{ marginBottom: '2rem' }}>
        <div style={{ display: 'flex', gap: '1rem' }}>
          <input
            type="text"
            value={newTodo}
            onChange={(e) => setNewTodo(e.target.value)}
            placeholder="Add a new todo..."
            style={{ flex: 1, padding: '0.75rem', border: '1px solid #ddd', borderRadius: '4px' }}
            disabled={loading}
          />
          <button 
            type="submit"
            disabled={loading || !newTodo.trim()}
            style={{
              backgroundColor: '#28a745',
              color: 'white',
              border: 'none',
              padding: '0.75rem 1.5rem',
              borderRadius: '4px',
              cursor: loading ? 'not-allowed' : 'pointer',
              opacity: loading ? 0.6 : 1
            }}
          >
            Add Todo
          </button>
        </div>
      </form>
      
      {/* Batch Actions */}
      {selectedTodos.length > 0 && (
        <div style={{
          backgroundColor: '#e2e3e5',
          padding: '1rem',
          borderRadius: '4px',
          marginBottom: '1rem',
          display: 'flex',
          justifyContent: 'space-between',
          alignItems: 'center'
        }}>
          <span>{selectedTodos.length} todos selected</span>
          <div style={{ display: 'flex', gap: '0.5rem' }}>
            <button 
              onClick={handleBatchComplete}
              style={{
                backgroundColor: '#28a745',
                color: 'white',
                border: 'none',
                padding: '0.5rem 1rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Mark Complete
            </button>
            <button 
              onClick={() => setSelectedTodos([])}
              style={{
                backgroundColor: '#6c757d',
                color: 'white',
                border: 'none',
                padding: '0.5rem 1rem',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Clear Selection
            </button>
          </div>
        </div>
      )}
      
      {/* Todo List */}
      <div>
        {todos.length === 0 ? (
          <p style={{ textAlign: 'center', color: '#666', padding: '2rem' }}>
            No todos yet. Add one above!
          </p>
        ) : (
          todos.map(todo => (
            <div
              key={todo.id}
              style={{
                display: 'flex',
                alignItems: 'center',
                padding: '1rem',
                border: '1px solid #ddd',
                borderRadius: '4px',
                marginBottom: '0.5rem',
                backgroundColor: selectedTodos.includes(todo.id) ? '#e3f2fd' : 
                                todo.completed ? '#f8f9fa' : 'white'
              }}
            >
              <input
                type="checkbox"
                checked={selectedTodos.includes(todo.id)}
                onChange={() => handleTodoSelect(todo.id)}
                style={{ marginRight: '1rem' }}
              />
              
              <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => dispatch(todoActions.toggleTodo(todo.id))}
                style={{ marginRight: '1rem' }}
              />
              
              <span 
                style={{ 
                  flex: 1, 
                  textDecoration: todo.completed ? 'line-through' : 'none',
                  color: todo.completed ? '#666' : '#333'
                }}
              >
                {todo.text}
              </span>
              
              <small style={{ color: '#666', marginRight: '1rem' }}>
                {new Date(todo.createdAt).toLocaleDateString()}
              </small>
              
              <button 
                onClick={() => dispatch(todoActions.deleteTodo(todo.id))}
                style={{
                  backgroundColor: '#dc3545',
                  color: 'white',
                  border: 'none',
                  padding: '0.25rem 0.5rem',
                  borderRadius: '4px',
                  cursor: 'pointer'
                }}
              >
                Delete
              </button>
            </div>
          ))
        )}
      </div>
    </div>
  );
}
```

**Example 2: Redux with Normalized State and Complex Selectors**
```jsx
// Normalized state structure for complex data
const initialNormalizedState = {
  users: {
    byId: {},
    allIds: []
  },
  posts: {
    byId: {},
    allIds: []
  },
  comments: {
    byId: {},
    allIds: []
  },
  ui: {
    loading: {
      users: false,
      posts: false,
      comments: false
    },
    errors: {
      users: null,
      posts: null,
      comments: null
    },
    selectedUserId: null,
    selectedPostId: null
  }
};

// Normalized reducer
function normalizedReducer(state = initialNormalizedState, action) {
  switch (action.type) {
    case 'FETCH_USERS_SUCCESS':
      return {
        ...state,
        users: {
          byId: action.payload.reduce((acc, user) => {
            acc[user.id] = user;
            return acc;
          }, {}),
          allIds: action.payload.map(user => user.id)
        }
      };
    
    case 'FETCH_POSTS_SUCCESS':
      return {
        ...state,
        posts: {
          byId: action.payload.reduce((acc, post) => {
            acc[post.id] = post;
            return acc;
          }, {}),
          allIds: action.payload.map(post => post.id)
        }
      };
    
    case 'ADD_COMMENT':
      const comment = action.payload;
      return {
        ...state,
        comments: {
          byId: {
            ...state.comments.byId,
            [comment.id]: comment
          },
          allIds: [...state.comments.allIds, comment.id]
        }
      };
    
    case 'SELECT_USER':
      return {
        ...state,
        ui: {
          ...state.ui,
          selectedUserId: action.payload
        }
      };
    
    case 'SELECT_POST':
      return {
        ...state,
        ui: {
          ...state.ui,
          selectedPostId: action.payload
        }
      };
    
    default:
      return state;
  }
}

// Complex selectors with memoization
import { createSelector } from 'reselect';

// Basic selectors
const getUsersById = (state) => state.users.byId;
const getUserIds = (state) => state.users.allIds;
const getPostsById = (state) => state.posts.byId;
const getPostIds = (state) => state.posts.allIds;
const getCommentsById = (state) => state.comments.byId;
const getCommentIds = (state) => state.comments.allIds;
const getSelectedUserId = (state) => state.ui.selectedUserId;
const getSelectedPostId = (state) => state.ui.selectedPostId;

// Memoized selectors
const getAllUsers = createSelector(
  [getUsersById, getUserIds],
  (usersById, userIds) => userIds.map(id => usersById[id])
);

const getAllPosts = createSelector(
  [getPostsById, getPostIds],
  (postsById, postIds) => postIds.map(id => postsById[id])
);

const getSelectedUser = createSelector(
  [getUsersById, getSelectedUserId],
  (usersById, selectedId) => selectedId ? usersById[selectedId] : null
);

const getSelectedPost = createSelector(
  [getPostsById, getSelectedPostId],
  (postsById, selectedId) => selectedId ? postsById[selectedId] : null
);

const getPostsByUser = createSelector(
  [getAllPosts, getSelectedUserId],
  (posts, userId) => userId ? posts.filter(post => post.userId === userId) : []
);

const getCommentsByPost = createSelector(
  [getCommentsById, getCommentIds, getSelectedPostId],
  (commentsById, commentIds, postId) => {
    if (!postId) return [];
    return commentIds
      .map(id => commentsById[id])
      .filter(comment => comment.postId === postId)
      .sort((a, b) => new Date(a.createdAt) - new Date(b.createdAt));
  }
);

const getUserStats = createSelector(
  [getAllPosts, getAllUsers, getCommentsById, getCommentIds],
  (posts, users, commentsById, commentIds) => {
    return users.map(user => {
      const userPosts = posts.filter(post => post.userId === user.id);
      const userComments = commentIds
        .map(id => commentsById[id])
        .filter(comment => comment.userId === user.id);
      
      return {
        ...user,
        postCount: userPosts.length,
        commentCount: userComments.length,
        totalLikes: userPosts.reduce((sum, post) => sum + (post.likes || 0), 0)
      };
    });
  }
);

// Component using complex selectors
function SocialMediaDashboard() {
  const dispatch = useDispatch();
  const {
    users,
    selectedUser,
    userPosts,
    selectedPost,
    postComments,
    userStats
  } = useSelector(state => ({
    users: getAllUsers(state),
    selectedUser: getSelectedUser(state),
    userPosts: getPostsByUser(state),
    selectedPost: getSelectedPost(state),
    postComments: getCommentsByPost(state),
    userStats: getUserStats(state)
  }));
  
  const [newComment, setNewComment] = useState('');
  
  useEffect(() => {
    // Fetch initial data
    dispatch(fetchUsers());
    dispatch(fetchPosts());
  }, [dispatch]);
  
  const handleAddComment = (e) => {
    e.preventDefault();
    if (newComment.trim() && selectedPost) {
      dispatch({
        type: 'ADD_COMMENT',
        payload: {
          id: Date.now(),
          postId: selectedPost.id,
          userId: 1, // Current user
          text: newComment.trim(),
          createdAt: new Date().toISOString()
        }
      });
      setNewComment('');
    }
  };
  
  return (
    <div style={{ display: 'flex', height: '100vh' }}>
      {/* Users Sidebar */}
      <div style={{ width: '300px', backgroundColor: '#f8f9fa', padding: '1rem', overflowY: 'auto' }}>
        <h3>Users</h3>
        {userStats.map(user => (
          <div
            key={user.id}
            onClick={() => dispatch({ type: 'SELECT_USER', payload: user.id })}
            style={{
              padding: '1rem',
              marginBottom: '0.5rem',
              backgroundColor: selectedUser?.id === user.id ? '#007bff' : 'white',
              color: selectedUser?.id === user.id ? 'white' : '#333',
              borderRadius: '4px',
              cursor: 'pointer',
              border: '1px solid #ddd'
            }}
          >
            <div style={{ fontWeight: 'bold' }}>{user.name}</div>
            <div style={{ fontSize: '0.9rem', opacity: 0.8 }}>
              {user.postCount} posts • {user.commentCount} comments • {user.totalLikes} likes
            </div>
          </div>
        ))}
      </div>
      
      {/* Posts Section */}
      <div style={{ flex: 1, padding: '1rem', overflowY: 'auto' }}>
        {selectedUser ? (
          <div>
            <h2>{selectedUser.name}'s Posts ({userPosts.length})</h2>
            {userPosts.length === 0 ? (
              <p>No posts yet.</p>
            ) : (
              userPosts.map(post => (
                <div
                  key={post.id}
                  onClick={() => dispatch({ type: 'SELECT_POST', payload: post.id })}
                  style={{
                    padding: '1.5rem',
                    marginBottom: '1rem',
                    backgroundColor: selectedPost?.id === post.id ? '#e3f2fd' : 'white',
                    border: '1px solid #ddd',
                    borderRadius: '8px',
                    cursor: 'pointer'
                  }}
                >
                  <h4>{post.title}</h4>
                  <p>{post.body}</p>
                  <div style={{ fontSize: '0.9rem', color: '#666', marginTop: '1rem' }}>
                    {post.likes || 0} likes • {new Date(post.createdAt).toLocaleDateString()}
                  </div>
                </div>
              ))
            )}
          </div>
        ) : (
          <div style={{ textAlign: 'center', color: '#666', marginTop: '2rem' }}>
            <h3>Select a user to view their posts</h3>
          </div>
        )}
      </div>
      
      {/* Comments Section */}
      <div style={{ width: '400px', backgroundColor: '#f8f9fa', padding: '1rem', overflowY: 'auto' }}>
        {selectedPost ? (
          <div>
            <h3>Comments ({postComments.length})</h3>
            
            {/* Add Comment Form */}
            <form onSubmit={handleAddComment} style={{ marginBottom: '1rem' }}>
              <textarea
                value={newComment}
                onChange={(e) => setNewComment(e.target.value)}
                placeholder="Add a comment..."
                style={{
                  width: '100%',
                  padding: '0.5rem',
                  border: '1px solid #ddd',
                  borderRadius: '4px',
                  resize: 'vertical',
                  minHeight: '80px'
                }}
              />
              <button
                type="submit"
                style={{
                  backgroundColor: '#007bff',
                  color: 'white',
                  border: 'none',
                  padding: '0.5rem 1rem',
                  borderRadius: '4px',
                  cursor: 'pointer',
                  marginTop: '0.5rem'
                }}
              >
                Add Comment
              </button>
            </form>
            
            {/* Comments List */}
            {postComments.length === 0 ? (
              <p>No comments yet.</p>
            ) : (
              postComments.map(comment => (
                <div
                  key={comment.id}
                  style={{
                    padding: '1rem',
                    marginBottom: '0.5rem',
                    backgroundColor: 'white',
                    border: '1px solid #ddd',
                    borderRadius: '4px'
                  }}
                >
                  <div style={{ fontWeight: 'bold', marginBottom: '0.5rem' }}>
                    User {comment.userId}
                  </div>
                  <p style={{ margin: '0 0 0.5rem 0' }}>{comment.text}</p>
                  <div style={{ fontSize: '0.8rem', color: '#666' }}>
                    {new Date(comment.createdAt).toLocaleString()}
                  </div>
                </div>
              ))
            )}
          </div>
        ) : (
          <div style={{ textAlign: 'center', color: '#666', marginTop: '2rem' }}>
            <h3>Select a post to view comments</h3>
          </div>
        )}
      </div>
    </div>
  );
}

// Async actions for normalized data
const fetchUsers = () => async (dispatch) => {
  dispatch({ type: 'FETCH_USERS_REQUEST' });
  try {
    const response = await fetch('/api/users');
    const users = await response.json();
    dispatch({ type: 'FETCH_USERS_SUCCESS', payload: users });
  } catch (error) {
    dispatch({ type: 'FETCH_USERS_FAILURE', payload: error.message });
  }
};

const fetchPosts = () => async (dispatch) => {
  dispatch({ type: 'FETCH_POSTS_REQUEST' });
  try {
    const response = await fetch('/api/posts');
    const posts = await response.json();
    dispatch({ type: 'FETCH_POSTS_SUCCESS', payload: posts });
  } catch (error) {
    dispatch({ type: 'FETCH_POSTS_FAILURE', payload: error.message });
  }
};
```

**Redux Best Practices and Patterns:**
```jsx
// 1. Action creators with FSA (Flux Standard Action) pattern
const createAction = (type) => (payload, meta) => ({
  type,
  payload,
  meta,
  error: payload instanceof Error
});

const createAsyncAction = (baseType) => ({
  request: createAction(`${baseType}_REQUEST`),
  success: createAction(`${baseType}_SUCCESS`),
  failure: createAction(`${baseType}_FAILURE`)
});

// 2. Reducer composition
const createReducer = (initialState, handlers) => {
  return (state = initialState, action) => {
    if (handlers.hasOwnProperty(action.type)) {
      return handlers[action.type](state, action);
    }
    return state;
  };
};

// 3. Middleware for logging
const loggerMiddleware = (store) => (next) => (action) => {
  console.group(action.type);
  console.info('dispatching', action);
  console.log('prev state', store.getState());
  const result = next(action);
  console.log('next state', store.getState());
  console.groupEnd();
  return result;
};

// 4. Error handling middleware
const errorMiddleware = (store) => (next) => (action) => {
  try {
    return next(action);
  } catch (error) {
    console.error('Redux error:', error);
    store.dispatch({
      type: 'GLOBAL_ERROR',
      payload: error.message
    });
    return error;
  }
};
```

**Interview Questions:**
1. What are the three core principles of Redux?
2. What is the difference between actions and action creators?
3. What makes a reducer function "pure"?
4. How do you handle async operations in Redux?
5. What is the purpose of middleware in Redux?
6. How do you optimize Redux performance?
7. What is the difference between Redux and Context API?
8. How do you structure a large Redux application?
9. What are selectors and why are they important?
10. How do you test Redux reducers and actions?

---##
# 🔹 Day 26–27: Redux Middleware - DEEP DIVE

**Definition (English):**
Redux middleware provides a third-party extension point between dispatching an action and the moment it reaches the reducer. Middleware can intercept, modify, delay, or even stop actions. It's commonly used for logging, crash reporting, async operations, routing, and other side effects. Middleware follows a curried function pattern and can be composed together to create powerful data flow pipelines.

**Hinglish Deep Explanation:**
Redux middleware ek powerful concept hai jo action aur reducer ke beech mein kaam karta hai. Ye action ko intercept kar sakta hai, modify kar sakta hai, delay kar sakta hai, ya completely stop bhi kar sakta hai. Middleware ka main use async operations (API calls), logging, error handling, aur side effects ke liye hota hai. Ye curried functions ka pattern follow karta hai aur multiple middleware ko chain kar sakte hain.

**Redux Middleware Deep Understanding:**

**1. Understanding Middleware Architecture:**
```jsx
// Middleware signature: store => next => action => result
// This is a curried function that receives store, then next, then action

// Basic middleware structure
const basicMiddleware = (store) => (next) => (action) => {
  // Before action reaches reducer
  console.log('Before:', action);
  
  // Call next middleware or reducer
  const result = next(action);
  
  // After action has been processed
  console.log('After:', store.getState());
  
  return result;
};

// Middleware composition example
import { createStore, applyMiddleware, compose } from 'redux';

const store = createStore(
  rootReducer,
  compose(
    applyMiddleware(
      loggerMiddleware,
      thunkMiddleware,
      errorMiddleware,
      customMiddleware
    ),
    window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
  )
);
```

**2. Custom Middleware Examples:**
```jsx
// 1. Advanced Logger Middleware
const advancedLoggerMiddleware = (store) => (next) => (action) => {
  const startTime = performance.now();
  const prevState = store.getState();
  
  console.group(`🚀 Action: ${action.type}`);
  console.log('📤 Dispatching:', action);
  console.log('📊 Previous State:', prevState);
  
  const result = next(action);
  
  const nextState = store.getState();
  const duration = performance.now() - startTime;
  
  console.log('📈 Next State:', nextState);
  console.log('⏱️ Duration:', `${duration.toFixed(2)}ms`);
  
  // Show state diff
  const stateDiff = getStateDiff(prevState, nextState);
  if (Object.keys(stateDiff).length > 0) {
    console.log('🔄 State Changes:', stateDiff);
  }
  
  console.groupEnd();
  
  return result;
};

// Helper function to calculate state differences
function getStateDiff(prevState, nextState) {
  const diff = {};
  
  function compareObjects(prev, next, path = '') {
    for (const key in next) {
      const currentPath = path ? `${path}.${key}` : key;
      
      if (prev[key] !== next[key]) {
        if (typeof next[key] === 'object' && next[key] !== null) {
          compareObjects(prev[key] || {}, next[key], currentPath);
        } else {
          diff[currentPath] = {
            from: prev[key],
            to: next[key]
          };
        }
      }
    }
  }
  
  compareObjects(prevState, nextState);
  return diff;
}

// 2. Error Handling Middleware
const errorHandlingMiddleware = (store) => (next) => (action) => {
  try {
    return next(action);
  } catch (error) {
    console.error('🚨 Redux Error:', error);
    
    // Dispatch error action
    store.dispatch({
      type: 'GLOBAL_ERROR',
      payload: {
        message: error.message,
        stack: error.stack,
        action: action,
        timestamp: new Date().toISOString()
      }
    });
    
    // Send to error reporting service
    if (typeof window !== 'undefined' && window.Sentry) {
      window.Sentry.captureException(error, {
        extra: {
          action,
          state: store.getState()
        }
      });
    }
    
    return error;
  }
};

// 3. API Middleware for standardized API calls
const API_REQUEST = 'API_REQUEST';
const API_SUCCESS = 'API_SUCCESS';
const API_FAILURE = 'API_FAILURE';

const apiMiddleware = (store) => (next) => (action) => {
  // Pass through non-API actions
  if (action.type !== API_REQUEST) {
    return next(action);
  }
  
  const {
    endpoint,
    method = 'GET',
    body,
    headers = {},
    types,
    meta = {}
  } = action.payload;
  
  const [requestType, successType, failureType] = types;
  
  // Dispatch request action
  store.dispatch({
    type: requestType,
    meta: { ...meta, loading: true }
  });
  
  // Make API call
  return fetch(endpoint, {
    method,
    headers: {
      'Content-Type': 'application/json',
      ...headers
    },
    body: body ? JSON.stringify(body) : undefined
  })
    .then(response => {
      if (!response.ok) {
        throw new Error(`HTTP ${response.status}: ${response.statusText}`);
      }
      return response.json();
    })
    .then(data => {
      // Dispatch success action
      store.dispatch({
        type: successType,
        payload: data,
        meta: { ...meta, loading: false }
      });
      return data;
    })
    .catch(error => {
      // Dispatch failure action
      store.dispatch({
        type: failureType,
        payload: error.message,
        error: true,
        meta: { ...meta, loading: false }
      });
      throw error;
    });
};

// 4. Caching Middleware
const cacheMiddleware = (store) => (next) => (action) => {
  const cache = new Map();
  const CACHE_DURATION = 5 * 60 * 1000; // 5 minutes
  
  return (action) => {
    // Only cache GET requests
    if (action.type === API_REQUEST && action.payload.method === 'GET') {
      const cacheKey = `${action.payload.endpoint}${JSON.stringify(action.payload.params || {})}`;
      const cached = cache.get(cacheKey);
      
      if (cached && Date.now() - cached.timestamp < CACHE_DURATION) {
        console.log('📦 Cache hit:', cacheKey);
        
        // Dispatch success with cached data
        const [, successType] = action.payload.types;
        store.dispatch({
          type: successType,
          payload: cached.data,
          meta: { ...action.payload.meta, fromCache: true }
        });
        
        return Promise.resolve(cached.data);
      }
      
      // Cache miss - proceed with request and cache result
      return next(action).then(data => {
        cache.set(cacheKey, {
          data,
          timestamp: Date.now()
        });
        return data;
      });
    }
    
    return next(action);
  };
};

// 5. Analytics Middleware
const analyticsMiddleware = (store) => (next) => (action) => {
  const result = next(action);
  
  // Track specific actions
  const trackableActions = [
    'USER_LOGIN',
    'USER_LOGOUT',
    'PRODUCT_VIEW',
    'PRODUCT_PURCHASE',
    'FORM_SUBMIT'
  ];
  
  if (trackableActions.includes(action.type)) {
    // Send to analytics service
    if (typeof window !== 'undefined' && window.gtag) {
      window.gtag('event', action.type, {
        custom_parameter: action.payload,
        timestamp: Date.now()
      });
    }
    
    // Custom analytics
    console.log('📊 Analytics Event:', {
      action: action.type,
      payload: action.payload,
      timestamp: new Date().toISOString(),
      userId: store.getState().user?.id
    });
  }
  
  return result;
};

// 6. Persistence Middleware
const persistenceMiddleware = (store) => (next) => (action) => {
  const result = next(action);
  
  // Actions that should trigger persistence
  const persistActions = [
    'USER_LOGIN',
    'USER_UPDATE_PROFILE',
    'SETTINGS_UPDATE',
    'THEME_CHANGE'
  ];
  
  if (persistActions.includes(action.type)) {
    const state = store.getState();
    
    // Save to localStorage
    try {
      localStorage.setItem('reduxState', JSON.stringify({
        user: state.user,
        settings: state.settings,
        theme: state.theme,
        timestamp: Date.now()
      }));
    } catch (error) {
      console.error('Failed to persist state:', error);
    }
  }
  
  return result;
};
```

**Example 1: Advanced Thunk Middleware Implementation**
```jsx
// Custom thunk middleware with enhanced features
const enhancedThunkMiddleware = (store) => (next) => (action) => {
  // If action is a function, call it with dispatch and getState
  if (typeof action === 'function') {
    return action(store.dispatch, store.getState, {
      // Extra argument with utilities
      api: {
        get: (url) => fetch(url).then(res => res.json()),
        post: (url, data) => fetch(url, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(data)
        }).then(res => res.json())
      },
      utils: {
        delay: (ms) => new Promise(resolve => setTimeout(resolve, ms)),
        retry: async (fn, retries = 3) => {
          for (let i = 0; i < retries; i++) {
            try {
              return await fn();
            } catch (error) {
              if (i === retries - 1) throw error;
              await new Promise(resolve => setTimeout(resolve, 1000 * (i + 1)));
            }
          }
        }
      }
    });
  }
  
  return next(action);
};

// Enhanced async action creators
const enhancedAsyncActions = {
  fetchUserWithRetry: (userId) => async (dispatch, getState, { api, utils }) => {
    dispatch({ type: 'FETCH_USER_REQUEST', payload: userId });
    
    try {
      const user = await utils.retry(
        () => api.get(`/api/users/${userId}`),
        3 // Retry 3 times
      );
      
      dispatch({ type: 'FETCH_USER_SUCCESS', payload: user });
      return user;
    } catch (error) {
      dispatch({ type: 'FETCH_USER_FAILURE', payload: error.message });
      throw error;
    }
  },
  
  fetchUserWithDelay: (userId, delay = 1000) => async (dispatch, getState, { api, utils }) => {
    dispatch({ type: 'FETCH_USER_REQUEST', payload: userId });
    
    // Add artificial delay
    await utils.delay(delay);
    
    try {
      const user = await api.get(`/api/users/${userId}`);
      dispatch({ type: 'FETCH_USER_SUCCESS', payload: user });
      return user;
    } catch (error) {
      dispatch({ type: 'FETCH_USER_FAILURE', payload: error.message });
      throw error;
    }
  },
  
  batchFetchUsers: (userIds) => async (dispatch, getState, { api }) => {
    dispatch({ type: 'BATCH_FETCH_USERS_REQUEST', payload: userIds });
    
    try {
      // Fetch users in parallel
      const userPromises = userIds.map(id => api.get(`/api/users/${id}`));
      const users = await Promise.all(userPromises);
      
      dispatch({ type: 'BATCH_FETCH_USERS_SUCCESS', payload: users });
      return users;
    } catch (error) {
      dispatch({ type: 'BATCH_FETCH_USERS_FAILURE', payload: error.message });
      throw error;
    }
  }
};

// Component using enhanced async actions
function EnhancedUserManager() {
  const dispatch = useDispatch();
  const { users, loading, error } = useSelector(state => state.users);
  const [selectedUserId, setSelectedUserId] = useState('');
  
  const handleFetchUser = async () => {
    if (!selectedUserId) return;
    
    try {
      await dispatch(enhancedAsyncActions.fetchUserWithRetry(selectedUserId));
    } catch (error) {
      console.error('Failed to fetch user:', error);
    }
  };
  
  const handleFetchUserWithDelay = async () => {
    if (!selectedUserId) return;
    
    try {
      await dispatch(enhancedAsyncActions.fetchUserWithDelay(selectedUserId, 2000));
    } catch (error) {
      console.error('Failed to fetch user:', error);
    }
  };
  
  const handleBatchFetch = async () => {
    const userIds = ['1', '2', '3', '4', '5'];
    
    try {
      await dispatch(enhancedAsyncActions.batchFetchUsers(userIds));
    } catch (error) {
      console.error('Failed to batch fetch users:', error);
    }
  };
  
  return (
    <div style={{ padding: '2rem', maxWidth: '600px', margin: '0 auto' }}>
      <h2>Enhanced User Manager</h2>
      
      {error && (
        <div style={{
          backgroundColor: '#f8d7da',
          color: '#721c24',
          padding: '1rem',
          borderRadius: '4px',
          marginBottom: '1rem'
        }}>
          Error: {error}
        </div>
      )}
      
      <div style={{ marginBottom: '2rem' }}>
        <input
          type="text"
          value={selectedUserId}
          onChange={(e) => setSelectedUserId(e.target.value)}
          placeholder="Enter user ID"
          style={{
            padding: '0.5rem',
            marginRight: '1rem',
            border: '1px solid #ddd',
            borderRadius: '4px'
          }}
        />
        
        <button 
          onClick={handleFetchUser}
          disabled={loading || !selectedUserId}
          style={{
            backgroundColor: '#007bff',
            color: 'white',
            border: 'none',
            padding: '0.5rem 1rem',
            borderRadius: '4px',
            cursor: 'pointer',
            marginRight: '0.5rem',
            opacity: loading ? 0.6 : 1
          }}
        >
          Fetch with Retry
        </button>
        
        <button 
          onClick={handleFetchUserWithDelay}
          disabled={loading || !selectedUserId}
          style={{
            backgroundColor: '#28a745',
            color: 'white',
            border: 'none',
            padding: '0.5rem 1rem',
            borderRadius: '4px',
            cursor: 'pointer',
            marginRight: '0.5rem',
            opacity: loading ? 0.6 : 1
          }}
        >
          Fetch with Delay
        </button>
        
        <button 
          onClick={handleBatchFetch}
          disabled={loading}
          style={{
            backgroundColor: '#ffc107',
            color: '#333',
            border: 'none',
            padding: '0.5rem 1rem',
            borderRadius: '4px',
            cursor: 'pointer',
            opacity: loading ? 0.6 : 1
          }}
        >
          Batch Fetch
        </button>
      </div>
      
      {loading && (
        <div style={{
          backgroundColor: '#d1ecf1',
          color: '#0c5460',
          padding: '1rem',
          borderRadius: '4px',
          marginBottom: '1rem',
          textAlign: 'center'
        }}>
          Loading...
        </div>
      )}
      
      <div>
        <h3>Users ({Object.keys(users).length})</h3>
        {Object.values(users).map(user => (
          <div
            key={user.id}
            style={{
              padding: '1rem',
              marginBottom: '0.5rem',
              backgroundColor: 'white',
              border: '1px solid #ddd',
              borderRadius: '4px'
            }}
          >
            <h4>{user.name}</h4>
            <p>Email: {user.email}</p>
            <p>ID: {user.id}</p>
          </div>
        ))}
      </div>
    </div>
  );
}
```

**Example 2: Redux Saga Alternative Implementation**
```jsx
// Custom saga-like middleware for complex async flows
const sagaMiddleware = (store) => (next) => (action) => {
  // Handle saga actions
  if (action.type && action.type.endsWith('_SAGA')) {
    const sagaType = action.type.replace('_SAGA', '');
    
    // Find and execute corresponding saga
    if (sagas[sagaType]) {
      sagas[sagaType](action.payload, {
        dispatch: store.dispatch,
        getState: store.getState,
        put: (action) => store.dispatch(action),
        call: (fn, ...args) => fn(...args),
        select: (selector) => selector(store.getState()),
        take: (actionType) => new Promise(resolve => {
          const unsubscribe = store.subscribe(() => {
            const state = store.getState();
            // Simplified take implementation
            resolve(state);
            unsubscribe();
          });
        })
      });
    }
    
    return;
  }
  
  return next(action);
};

// Saga definitions
const sagas = {
  FETCH_USER_PROFILE: async function* (userId, { put, call, select }) {
    try {
      yield put({ type: 'FETCH_USER_PROFILE_REQUEST' });
      
      // Check if user is already in cache
      const cachedUser = yield select(state => state.users.byId[userId]);
      if (cachedUser) {
        yield put({ type: 'FETCH_USER_PROFILE_SUCCESS', payload: cachedUser });
        return;
      }
      
      // Fetch user profile
      const user = yield call(fetch, `/api/users/${userId}`);
      const userData = yield call([user, 'json']);
      
      yield put({ type: 'FETCH_USER_PROFILE_SUCCESS', payload: userData });
      
      // Fetch user posts in parallel
      yield put({ type: 'FETCH_USER_POSTS_SAGA', payload: userId });
      
    } catch (error) {
      yield put({ type: 'FETCH_USER_PROFILE_FAILURE', payload: error.message });
    }
  },
  
  FETCH_USER_POSTS: async function* (userId, { put, call }) {
    try {
      yield put({ type: 'FETCH_USER_POSTS_REQUEST' });
      
      const posts = yield call(fetch, `/api/users/${userId}/posts`);
      const postsData = yield call([posts, 'json']);
      
      yield put({ type: 'FETCH_USER_POSTS_SUCCESS', payload: postsData });
      
    } catch (error) {
      yield put({ type: 'FETCH_USER_POSTS_FAILURE', payload: error.message });
    }
  },
  
  LOGIN_FLOW: async function* (credentials, { put, call, select }) {
    try {
      yield put({ type: 'LOGIN_REQUEST' });
      
      // Attempt login
      const response = yield call(fetch, '/api/auth/login', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(credentials)
      });
      
      if (!response.ok) {
        throw new Error('Login failed');
      }
      
      const { user, token } = yield call([response, 'json']);
      
      // Store token
      localStorage.setItem('authToken', token);
      
      yield put({ type: 'LOGIN_SUCCESS', payload: user });
      
      // Fetch user profile after successful login
      yield put({ type: 'FETCH_USER_PROFILE_SAGA', payload: user.id });
      
      // Track login event
      yield put({ type: 'TRACK_EVENT', payload: { event: 'user_login', userId: user.id } });
      
    } catch (error) {
      yield put({ type: 'LOGIN_FAILURE', payload: error.message });
    }
  }
};

// Usage in components
function SagaExample() {
  const dispatch = useDispatch();
  const { user, loading, error } = useSelector(state => state.user);
  
  const handleLogin = () => {
    dispatch({
      type: 'LOGIN_FLOW_SAGA',
      payload: { email: 'user@example.com', password: 'password' }
    });
  };
  
  const handleFetchProfile = () => {
    dispatch({
      type: 'FETCH_USER_PROFILE_SAGA',
      payload: '123'
    });
  };
  
  return (
    <div style={{ padding: '2rem' }}>
      <h2>Saga-like Middleware Example</h2>
      
      <button onClick={handleLogin} disabled={loading}>
        {loading ? 'Logging in...' : 'Login'}
      </button>
      
      <button onClick={handleFetchProfile} disabled={loading}>
        Fetch Profile
      </button>
      
      {error && <div style={{ color: 'red' }}>Error: {error}</div>}
      {user && <div>Welcome, {user.name}!</div>}
    </div>
  );
}
```

**Example 3: Real-time Middleware with WebSockets**
```jsx
// WebSocket middleware for real-time updates
const websocketMiddleware = (store) => (next) => (action) => {
  let socket = null;
  
  const connect = (url) => {
    socket = new WebSocket(url);
    
    socket.onopen = () => {
      console.log('🔌 WebSocket connected');
      store.dispatch({ type: 'WEBSOCKET_CONNECTED' });
    };
    
    socket.onmessage = (event) => {
      const data = JSON.parse(event.data);
      console.log('📨 WebSocket message:', data);
      
      // Dispatch received data as actions
      store.dispatch({
        type: 'WEBSOCKET_MESSAGE',
        payload: data
      });
      
      // Handle specific message types
      if (data.type) {
        store.dispatch({
          type: data.type,
          payload: data.payload
        });
      }
    };
    
    socket.onclose = () => {
      console.log('🔌 WebSocket disconnected');
      store.dispatch({ type: 'WEBSOCKET_DISCONNECTED' });
      
      // Attempt to reconnect after 3 seconds
      setTimeout(() => {
        if (store.getState().websocket.shouldReconnect) {
          connect(url);
        }
      }, 3000);
    };
    
    socket.onerror = (error) => {
      console.error('🚨 WebSocket error:', error);
      store.dispatch({ type: 'WEBSOCKET_ERROR', payload: error.message });
    };
  };
  
  const disconnect = () => {
    if (socket) {
      socket.close();
      socket = null;
    }
  };
  
  const send = (data) => {
    if (socket && socket.readyState === WebSocket.OPEN) {
      socket.send(JSON.stringify(data));
    }
  };
  
  // Handle WebSocket actions
  switch (action.type) {
    case 'WEBSOCKET_CONNECT':
      connect(action.payload.url);
      break;
      
    case 'WEBSOCKET_DISCONNECT':
      disconnect();
      break;
      
    case 'WEBSOCKET_SEND':
      send(action.payload);
      break;
      
    default:
      return next(action);
  }
};

// WebSocket action creators
const websocketActions = {
  connect: (url) => ({
    type: 'WEBSOCKET_CONNECT',
    payload: { url }
  }),
  
  disconnect: () => ({
    type: 'WEBSOCKET_DISCONNECT'
  }),
  
  send: (data) => ({
    type: 'WEBSOCKET_SEND',
    payload: data
  })
};

// Real-time chat component
function RealTimeChatApp() {
  const dispatch = useDispatch();
  const { 
    messages, 
    connected, 
    users 
  } = useSelector(state => ({
    messages: state.chat.messages,
    connected: state.websocket.connected,
    users: state.chat.users
  }));
  
  const [message, setMessage] = useState('');
  const [username, setUsername] = useState('');
  
  useEffect(() => {
    // Connect to WebSocket when component mounts
    dispatch(websocketActions.connect('ws://localhost:8080/chat'));
    
    return () => {
      // Disconnect when component unmounts
      dispatch(websocketActions.disconnect());
    };
  }, [dispatch]);
  
  const handleSendMessage = (e) => {
    e.preventDefault();
    
    if (message.trim() && username.trim()) {
      dispatch(websocketActions.send({
        type: 'CHAT_MESSAGE',
        payload: {
          id: Date.now(),
          username,
          message: message.trim(),
          timestamp: new Date().toISOString()
        }
      }));
      
      setMessage('');
    }
  };
  
  const handleJoinChat = () => {
    if (username.trim()) {
      dispatch(websocketActions.send({
        type: 'USER_JOIN',
        payload: {
          username: username.trim(),
          timestamp: new Date().toISOString()
        }
      }));
    }
  };
  
  return (
    <div style={{ maxWidth: '600px', margin: '2rem auto', padding: '2rem' }}>
      <h2>Real-time Chat</h2>
      
      <div style={{
        padding: '1rem',
        backgroundColor: connected ? '#d4edda' : '#f8d7da',
        color: connected ? '#155724' : '#721c24',
        borderRadius: '4px',
        marginBottom: '1rem'
      }}>
        Status: {connected ? '🟢 Connected' : '🔴 Disconnected'}
      </div>
      
      {!username && (
        <div style={{ marginBottom: '2rem' }}>
          <input
            type="text"
            placeholder="Enter your username"
            value={username}
            onChange={(e) => setUsername(e.target.value)}
            onKeyPress={(e) => e.key === 'Enter' && handleJoinChat()}
            style={{
              padding: '0.5rem',
              marginRight: '1rem',
              border: '1px solid #ddd',
              borderRadius: '4px'
            }}
          />
          <button 
            onClick={handleJoinChat}
            style={{
              backgroundColor: '#007bff',
              color: 'white',
              border: 'none',
              padding: '0.5rem 1rem',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            Join Chat
          </button>
        </div>
      )}
      
      {username && (
        <>
          <div style={{
            height: '300px',
            overflowY: 'auto',
            border: '1px solid #ddd',
            borderRadius: '4px',
            padding: '1rem',
            marginBottom: '1rem',
            backgroundColor: '#f8f9fa'
          }}>
            {messages.map(msg => (
              <div key={msg.id} style={{ marginBottom: '0.5rem' }}>
                <strong>{msg.username}:</strong> {msg.message}
                <small style={{ color: '#666', marginLeft: '1rem' }}>
                  {new Date(msg.timestamp).toLocaleTimeString()}
                </small>
              </div>
            ))}
          </div>
          
          <form onSubmit={handleSendMessage}>
            <div style={{ display: 'flex', gap: '1rem' }}>
              <input
                type="text"
                value={message}
                onChange={(e) => setMessage(e.target.value)}
                placeholder="Type your message..."
                style={{
                  flex: 1,
                  padding: '0.5rem',
                  border: '1px solid #ddd',
                  borderRadius: '4px'
                }}
                disabled={!connected}
              />
              <button
                type="submit"
                disabled={!connected || !message.trim()}
                style={{
                  backgroundColor: '#28a745',
                  color: 'white',
                  border: 'none',
                  padding: '0.5rem 1rem',
                  borderRadius: '4px',
                  cursor: 'pointer',
                  opacity: (!connected || !message.trim()) ? 0.6 : 1
                }}
              >
                Send
              </button>
            </div>
          </form>
          
          <div style={{ marginTop: '1rem' }}>
            <h4>Online Users ({users.length})</h4>
            <div style={{ display: 'flex', gap: '0.5rem', flexWrap: 'wrap' }}>
              {users.map(user => (
                <span
                  key={user.username}
                  style={{
                    backgroundColor: '#e9ecef',
                    padding: '0.25rem 0.5rem',
                    borderRadius: '12px',
                    fontSize: '0.9rem'
                  }}
                >
                  {user.username}
                </span>
              ))}
            </div>
          </div>
        </>
      )}
    </div>
  );
}
```

**Middleware Best Practices and Patterns:**
```jsx
// 1. Conditional middleware application
const conditionalMiddleware = (condition, middleware) => (store) => (next) => (action) => {
  if (condition(store.getState(), action)) {
    return middleware(store)(next)(action);
  }
  return next(action);
};

// Usage
const devOnlyLogger = conditionalMiddleware(
  () => process.env.NODE_ENV === 'development',
  loggerMiddleware
);

// 2. Middleware with configuration
const createConfigurableMiddleware = (config) => (store) => (next) => (action) => {
  if (config.enabled) {
    // Apply middleware logic
    console.log('Configured middleware:', config);
  }
  return next(action);
};

// 3. Async middleware with cancellation
const cancellableAsyncMiddleware = (store) => (next) => (action) => {
  const pendingRequests = new Map();
  
  return (action) => {
    if (action.type === 'CANCEL_REQUEST') {
      const request = pendingRequests.get(action.payload.requestId);
      if (request) {
        request.cancel();
        pendingRequests.delete(action.payload.requestId);
      }
      return;
    }
    
    if (action.meta && action.meta.cancellable) {
      const requestId = action.meta.requestId || Date.now();
      let cancelled = false;
      
      const cancellablePromise = {
        cancel: () => { cancelled = true; }
      };
      
      pendingRequests.set(requestId, cancellablePromise);
      
      const result = next(action);
      
      if (result && typeof result.then === 'function') {
        return result.then(
          (value) => {
            pendingRequests.delete(requestId);
            return cancelled ? Promise.reject(new Error('Cancelled')) : value;
          },
          (error) => {
            pendingRequests.delete(requestId);
            return cancelled ? Promise.reject(new Error('Cancelled')) : Promise.reject(error);
          }
        );
      }
      
      return result;
    }
    
    return next(action);
  };
};

// 4. Middleware composition utility
const composeMiddleware = (...middlewares) => (store) => (next) => (action) => {
  return middlewares.reduceRight(
    (composed, middleware) => middleware(store)(composed),
    next
  )(action);
};
```

**Interview Questions:**
1. What is Redux middleware and how does it work?
2. How do you create custom middleware in Redux?
3. What is the middleware signature and why is it curried?
4. How does Redux Thunk work internally?
5. What are some common use cases for middleware?
6. How do you handle errors in middleware?
7. What is the difference between middleware and enhancers?
8. How do you test Redux middleware?
9. How do you compose multiple middlewares?
10. What are some popular Redux middleware libraries?

---### 🔹 
Day 28: Reselect - DEEP DIVE

**Definition (English):**
Reselect is a library for creating memoized selector functions in Redux applications. It helps optimize performance by preventing unnecessary recalculations and re-renders. Selectors compute derived data from Redux state, and Reselect ensures these computations only happen when the input state actually changes, using memoization techniques.

**Hinglish Deep Explanation:**
Reselect ek performance optimization library hai jo Redux ke saath use hoti hai. Ye selectors ko memoize karta hai, matlab agar input state change nahi hua to calculation dobara nahi karega. Isse unnecessary re-renders aur expensive computations se bach sakte hain. Ye especially useful hai jab complex data transformations ya filtering operations karne hote hain.

**Reselect Deep Understanding:**

**1. Basic Reselect Concepts:**
```jsx
import { createSelector } from 'reselect';

// Input selectors - extract pieces of state
const getUsers = (state) => state.users.items;
const getUsersLoading = (state) => state.users.loading;
const getCurrentFilter = (state) => state.users.filter;
const getSearchTerm = (state) => state.users.searchTerm;
const getSortBy = (state) => state.users.sortBy;
const getSortOrder = (state) => state.users.sortOrder;

// Basic memoized selector
const getFilteredUsers = createSelector(
  [getUsers, getCurrentFilter],
  (users, filter) => {
    console.log('🔄 Calculating filtered users'); // Only logs when inputs change
    
    switch (filter) {
      case 'ACTIVE':
        return users.filter(user => user.isActive);
      case 'INACTIVE':
        return users.filter(user => !user.isActive);
      case 'PREMIUM':
        return users.filter(user => user.isPremium);
      default:
        return users;
    }
  }
);

// Complex selector with multiple inputs
const getSearchedAndFilteredUsers = createSelector(
  [getFilteredUsers, getSearchTerm],
  (filteredUsers, searchTerm) => {
    console.log('🔍 Calculating searched users');
    
    if (!searchTerm) return filteredUsers;
    
    const lowercaseSearch = searchTerm.toLowerCase();
    return filteredUsers.filter(user =>
      user.name.toLowerCase().includes(lowercaseSearch) ||
      user.email.toLowerCase().includes(lowercaseSearch) ||
      user.role.toLowerCase().includes(lowercaseSearch)
    );
  }
);

// Sorted selector
const getSortedUsers = createSelector(
  [getSearchedAndFilteredUsers, getSortBy, getSortOrder],
  (users, sortBy, sortOrder) => {
    console.log('📊 Calculating sorted users');
    
    const sortedUsers = [...users].sort((a, b) => {
      let aValue = a[sortBy];
      let bValue = b[sortBy];
      
      // Handle different data types
      if (typeof aValue === 'string') {
        aValue = aValue.toLowerCase();
        bValue = bValue.toLowerCase();
      }
      
      if (aValue < bValue) return sortOrder === 'asc' ? -1 : 1;
      if (aValue > bValue) return sortOrder === 'asc' ? 1 : -1;
      return 0;
    });
    
    return sortedUsers;
  }
);

// Selector with complex calculations
const getUserStatistics = createSelector(
  [getUsers],
  (users) => {
    console.log('📈 Calculating user statistics');
    
    const totalUsers = users.length;
    const activeUsers = users.filter(user => user.isActive).length;
    const premiumUsers = users.filter(user => user.isPremium).length;
    const averageAge = users.reduce((sum, user) => sum + (user.age || 0), 0) / totalUsers;
    
    const roleDistribution = users.reduce((acc, user) => {
      acc[user.role] = (acc[user.role] || 0) + 1;
      return acc;
    }, {});
    
    const locationDistribution = users.reduce((acc, user) => {
      const location = user.location || 'Unknown';
      acc[location] = (acc[location] || 0) + 1;
      return acc;
    }, {});
    
    return {
      totalUsers,
      activeUsers,
      inactiveUsers: totalUsers - activeUsers,
      premiumUsers,
      freeUsers: totalUsers - premiumUsers,
      averageAge: Math.round(averageAge * 100) / 100,
      roleDistribution,
      locationDistribution,
      activePercentage: Math.round((activeUsers / totalUsers) * 100),
      premiumPercentage: Math.round((premiumUsers / totalUsers) * 100)
    };
  }
);
```

**Example 1: Advanced E-commerce Selectors**
```jsx
// E-commerce state structure
const ecommerceState = {
  products: {
    items: [],
    categories: [],
    loading: false
  },
  cart: {
    items: [],
    discounts: [],
    shippingMethod: null
  },
  user: {
    profile: null,
    preferences: {},
    loyaltyPoints: 0
  },
  ui: {
    filters: {
      category: 'all',
      priceRange: { min: 0, max: 10000 },
      rating: 0,
      inStock: false
    },
    sorting: {
      field: 'name',
      order: 'asc'
    }
  }
};

// Input selectors
const getProducts = (state) => state.products.items;
const getCategories = (state) => state.products.categories;
const getCartItems = (state) => state.cart.items;
const getDiscounts = (state) => state.cart.discounts;
const getShippingMethod = (state) => state.cart.shippingMethod;
const getUserProfile = (state) => state.user.profile;
const getLoyaltyPoints = (state) => state.user.loyaltyPoints;
const getFilters = (state) => state.ui.filters;
const getSorting = (state) => state.ui.sorting;

// Product selectors
const getFilteredProducts = createSelector(
  [getProducts, getFilters],
  (products, filters) => {
    console.log('🛍️ Filtering products');
    
    return products.filter(product => {
      // Category filter
      if (filters.category !== 'all' && product.category !== filters.category) {
        return false;
      }
      
      // Price range filter
      if (product.price < filters.priceRange.min || product.price > filters.priceRange.max) {
        return false;
      }
      
      // Rating filter
      if (product.rating < filters.rating) {
        return false;
      }
      
      // Stock filter
      if (filters.inStock && product.stock <= 0) {
        return false;
      }
      
      return true;
    });
  }
);

const getSortedProducts = createSelector(
  [getFilteredProducts, getSorting],
  (products, sorting) => {
    console.log('📊 Sorting products');
    
    return [...products].sort((a, b) => {
      let aValue = a[sorting.field];
      let bValue = b[sorting.field];
      
      // Special handling for different fields
      if (sorting.field === 'name') {
        aValue = aValue.toLowerCase();
        bValue = bValue.toLowerCase();
      }
      
      if (sorting.order === 'asc') {
        return aValue < bValue ? -1 : aValue > bValue ? 1 : 0;
      } else {
        return aValue > bValue ? -1 : aValue < bValue ? 1 : 0;
      }
    });
  }
);

// Cart selectors
const getCartItemsWithDetails = createSelector(
  [getCartItems, getProducts],
  (cartItems, products) => {
    console.log('🛒 Calculating cart items with details');
    
    return cartItems.map(cartItem => {
      const product = products.find(p => p.id === cartItem.productId);
      return {
        ...cartItem,
        product,
        subtotal: product ? product.price * cartItem.quantity : 0
      };
    });
  }
);

const getCartSubtotal = createSelector(
  [getCartItemsWithDetails],
  (cartItems) => {
    console.log('💰 Calculating cart subtotal');
    return cartItems.reduce((total, item) => total + item.subtotal, 0);
  }
);

const getApplicableDiscounts = createSelector(
  [getDiscounts, getCartSubtotal, getLoyaltyPoints],
  (discounts, subtotal, loyaltyPoints) => {
    console.log('🎫 Calculating applicable discounts');
    
    return discounts.filter(discount => {
      // Check minimum order amount
      if (discount.minOrderAmount && subtotal < discount.minOrderAmount) {
        return false;
      }
      
      // Check loyalty points requirement
      if (discount.requiredLoyaltyPoints && loyaltyPoints < discount.requiredLoyaltyPoints) {
        return false;
      }
      
      // Check expiry date
      if (discount.expiryDate && new Date() > new Date(discount.expiryDate)) {
        return false;
      }
      
      return true;
    });
  }
);

const getBestDiscount = createSelector(
  [getApplicableDiscounts, getCartSubtotal],
  (discounts, subtotal) => {
    console.log('🏆 Finding best discount');
    
    if (discounts.length === 0) return null;
    
    return discounts.reduce((best, current) => {
      const currentSaving = current.type === 'percentage' 
        ? (subtotal * current.value) / 100
        : current.value;
      
      const bestSaving = best.type === 'percentage'
        ? (subtotal * best.value) / 100
        : best.value;
      
      return currentSaving > bestSaving ? current : best;
    });
  }
);

const getCartTotal = createSelector(
  [getCartSubtotal, getBestDiscount, getShippingMethod],
  (subtotal, discount, shippingMethod) => {
    console.log('🧾 Calculating cart total');
    
    let discountAmount = 0;
    if (discount) {
      discountAmount = discount.type === 'percentage'
        ? (subtotal * discount.value) / 100
        : discount.value;
    }
    
    const shippingCost = shippingMethod ? shippingMethod.cost : 0;
    const tax = (subtotal - discountAmount) * 0.1; // 10% tax
    
    return {
      subtotal,
      discountAmount,
      shippingCost,
      tax,
      total: subtotal - discountAmount + shippingCost + tax
    };
  }
);

// Analytics selectors
const getProductAnalytics = createSelector(
  [getProducts, getCartItems],
  (products, cartItems) => {
    console.log('📊 Calculating product analytics');
    
    const categoryStats = products.reduce((acc, product) => {
      if (!acc[product.category]) {
        acc[product.category] = {
          count: 0,
          totalValue: 0,
          averagePrice: 0,
          averageRating: 0
        };
      }
      
      acc[product.category].count++;
      acc[product.category].totalValue += product.price;
      acc[product.category].averageRating += product.rating;
      
      return acc;
    }, {});
    
    // Calculate averages
    Object.keys(categoryStats).forEach(category => {
      const stats = categoryStats[category];
      stats.averagePrice = stats.totalValue / stats.count;
      stats.averageRating = stats.averageRating / stats.count;
    });
    
    // Most popular products (by cart additions)
    const productPopularity = cartItems.reduce((acc, item) => {
      acc[item.productId] = (acc[item.productId] || 0) + item.quantity;
      return acc;
    }, {});
    
    const popularProducts = Object.entries(productPopularity)
      .sort(([, a], [, b]) => b - a)
      .slice(0, 5)
      .map(([productId, quantity]) => ({
        product: products.find(p => p.id === parseInt(productId)),
        totalQuantity: quantity
      }));
    
    return {
      categoryStats,
      popularProducts,
      totalProducts: products.length,
      averagePrice: products.reduce((sum, p) => sum + p.price, 0) / products.length,
      averageRating: products.reduce((sum, p) => sum + p.rating, 0) / products.length
    };
  }
);

// Component using advanced selectors
function EcommerceAnalyticsDashboard() {
  const {
    products,
    cartTotal,
    productAnalytics,
    applicableDiscounts,
    bestDiscount
  } = useSelector(state => ({
    products: getSortedProducts(state),
    cartTotal: getCartTotal(state),
    productAnalytics: getProductAnalytics(state),
    applicableDiscounts: getApplicableDiscounts(state),
    bestDiscount: getBestDiscount(state)
  }));
  
  return (
    <div style={{ padding: '2rem', maxWidth: '1200px', margin: '0 auto' }}>
      <h2>E-commerce Analytics Dashboard</h2>
      
      {/* Cart Summary */}
      <div style={{
        backgroundColor: '#f8f9fa',
        padding: '1.5rem',
        borderRadius: '8px',
        marginBottom: '2rem'
      }}>
        <h3>Cart Summary</h3>
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', gap: '1rem' }}>
          <div>
            <strong>Subtotal:</strong> ₹{cartTotal.subtotal?.toFixed(2)}
          </div>
          <div>
            <strong>Discount:</strong> -₹{cartTotal.discountAmount?.toFixed(2)}
          </div>
          <div>
            <strong>Shipping:</strong> ₹{cartTotal.shippingCost?.toFixed(2)}
          </div>
          <div>
            <strong>Tax:</strong> ₹{cartTotal.tax?.toFixed(2)}
          </div>
          <div style={{ fontSize: '1.2rem', color: '#007bff' }}>
            <strong>Total:</strong> ₹{cartTotal.total?.toFixed(2)}
          </div>
        </div>
        
        {bestDiscount && (
          <div style={{
            backgroundColor: '#d4edda',
            color: '#155724',
            padding: '0.5rem',
            borderRadius: '4px',
            marginTop: '1rem'
          }}>
            🎉 Best discount applied: {bestDiscount.name} 
            (Save ₹{cartTotal.discountAmount?.toFixed(2)})
          </div>
        )}
      </div>
      
      {/* Product Analytics */}
      <div style={{
        backgroundColor: 'white',
        padding: '1.5rem',
        borderRadius: '8px',
        border: '1px solid #dee2e6',
        marginBottom: '2rem'
      }}>
        <h3>Product Analytics</h3>
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', gap: '1rem' }}>
          <div>
            <h4>Overview</h4>
            <p>Total Products: {productAnalytics.totalProducts}</p>
            <p>Average Price: ₹{productAnalytics.averagePrice?.toFixed(2)}</p>
            <p>Average Rating: {productAnalytics.averageRating?.toFixed(1)} ⭐</p>
          </div>
          
          <div>
            <h4>Popular Products</h4>
            {productAnalytics.popularProducts?.map((item, index) => (
              <div key={item.product?.id} style={{ marginBottom: '0.5rem' }}>
                {index + 1}. {item.product?.name} ({item.totalQuantity} sold)
              </div>
            ))}
          </div>
        </div>
        
        <div style={{ marginTop: '1rem' }}>
          <h4>Category Statistics</h4>
          <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', gap: '1rem' }}>
            {Object.entries(productAnalytics.categoryStats || {}).map(([category, stats]) => (
              <div key={category} style={{
                backgroundColor: '#f8f9fa',
                padding: '1rem',
                borderRadius: '4px'
              }}>
                <h5>{category}</h5>
                <p>Products: {stats.count}</p>
                <p>Avg Price: ₹{stats.averagePrice?.toFixed(2)}</p>
                <p>Avg Rating: {stats.averageRating?.toFixed(1)} ⭐</p>
              </div>
            ))}
          </div>
        </div>
      </div>
      
      {/* Available Discounts */}
      {applicableDiscounts.length > 0 && (
        <div style={{
          backgroundColor: '#fff3cd',
          border: '1px solid #ffeaa7',
          padding: '1.5rem',
          borderRadius: '8px'
        }}>
          <h3>Available Discounts ({applicableDiscounts.length})</h3>
          <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', gap: '1rem' }}>
            {applicableDiscounts.map(discount => (
              <div key={discount.id} style={{
                backgroundColor: 'white',
                padding: '1rem',
                borderRadius: '4px',
                border: '1px solid #dee2e6'
              }}>
                <h4>{discount.name}</h4>
                <p>{discount.description}</p>
                <p>
                  <strong>
                    {discount.type === 'percentage' 
                      ? `${discount.value}% off` 
                      : `₹${discount.value} off`
                    }
                  </strong>
                </p>
                {discount.minOrderAmount && (
                  <small>Min order: ₹{discount.minOrderAmount}</small>
                )}
              </div>
            ))}
          </div>
        </div>
      )}
    </div>
  );
}
```

**Example 2: Performance Comparison and Optimization**
```jsx
// Performance comparison: With and without Reselect
function PerformanceComparison() {
  const [renderCount, setRenderCount] = useState(0);
  const [lastCalculation, setLastCalculation] = useState(null);
  
  // Without Reselect - recalculates every time
  const expensiveCalculationWithoutMemoization = useSelector(state => {
    console.log('🐌 Expensive calculation WITHOUT memoization');
    const start = performance.now();
    
    // Simulate expensive calculation
    const result = state.data.items
      .filter(item => item.active)
      .map(item => ({
        ...item,
        computed: item.value * Math.random() // Expensive operation
      }))
      .sort((a, b) => b.computed - a.computed);
    
    const duration = performance.now() - start;
    setLastCalculation({ type: 'without', duration, timestamp: Date.now() });
    
    return result;
  });
  
  // With Reselect - only recalculates when input changes
  const expensiveCalculationWithMemoization = useSelector(
    createSelector(
      [state => state.data.items],
      (items) => {
        console.log('⚡ Expensive calculation WITH memoization');
        const start = performance.now();
        
        const result = items
          .filter(item => item.active)
          .map(item => ({
            ...item,
            computed: item.value * Math.random()
          }))
          .sort((a, b) => b.computed - a.computed);
        
        const duration = performance.now() - start;
        setLastCalculation({ type: 'with', duration, timestamp: Date.now() });
        
        return result;
      }
    )
  );
  
  useEffect(() => {
    setRenderCount(prev => prev + 1);
  });
  
  return (
    <div style={{ padding: '2rem' }}>
      <h2>Performance Comparison</h2>
      <p>Render count: {renderCount}</p>
      
      {lastCalculation && (
        <div style={{
          backgroundColor: lastCalculation.type === 'with' ? '#d4edda' : '#f8d7da',
          padding: '1rem',
          borderRadius: '4px',
          marginBottom: '1rem'
        }}>
          Last calculation: {lastCalculation.type === 'with' ? 'WITH' : 'WITHOUT'} memoization
          <br />
          Duration: {lastCalculation.duration.toFixed(2)}ms
          <br />
          Time: {new Date(lastCalculation.timestamp).toLocaleTimeString()}
        </div>
      )}
      
      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '2rem' }}>
        <div>
          <h3>Without Reselect</h3>
          <p>Recalculates on every render</p>
          <p>Items: {expensiveCalculationWithoutMemoization.length}</p>
        </div>
        
        <div>
          <h3>With Reselect</h3>
          <p>Only recalculates when input changes</p>
          <p>Items: {expensiveCalculationWithMemoization.length}</p>
        </div>
      </div>
    </div>
  );
}
```

**Example 3: Advanced Selector Patterns**
```jsx
// 1. Parametric selectors
const makeGetUserById = () => createSelector(
  [getUsers, (state, userId) => userId],
  (users, userId) => users.find(user => user.id === userId)
);

// Usage with different instances
const getUserById1 = makeGetUserById();
const getUserById2 = makeGetUserById();

// 2. Selector factories
const createFilterSelector = (filterFn, name) => createSelector(
  [getUsers],
  (users) => {
    console.log(`🔍 Filtering users: ${name}`);
    return users.filter(filterFn);
  }
);

const getActiveUsers = createFilterSelector(user => user.isActive, 'active');
const getPremiumUsers = createFilterSelector(user => user.isPremium, 'premium');
const getAdminUsers = createFilterSelector(user => user.role === 'admin', 'admin');

// 3. Composed selectors
const getUsersWithStats = createSelector(
  [getUsers],
  (users) => {
    console.log('📊 Adding stats to users');
    return users.map(user => ({
      ...user,
      stats: {
        postsCount: Math.floor(Math.random() * 100),
        followersCount: Math.floor(Math.random() * 1000),
        likesCount: Math.floor(Math.random() * 5000)
      }
    }));
  }
);

const getTopUsers = createSelector(
  [getUsersWithStats],
  (usersWithStats) => {
    console.log('🏆 Finding top users');
    return usersWithStats
      .sort((a, b) => b.stats.followersCount - a.stats.followersCount)
      .slice(0, 10);
  }
);

// 4. Selector with custom equality check
const getExpensiveData = createSelector(
  [state => state.data.items],
  (items) => {
    console.log('💰 Expensive data processing');
    return items.map(item => ({
      ...item,
      processed: true,
      timestamp: Date.now()
    }));
  },
  {
    // Custom equality check
    memoizeOptions: {
      equalityCheck: (a, b) => {
        // Only recalculate if array length changes or items are different
        return a.length === b.length && a.every((item, index) => item.id === b[index]?.id);
      }
    }
  }
);

// 5. Async selector pattern (with middleware)
const createAsyncSelector = (asyncFn, dependencies) => {
  let cache = new Map();
  
  return createSelector(
    dependencies,
    (...args) => {
      const key = JSON.stringify(args);
      
      if (cache.has(key)) {
        return cache.get(key);
      }
      
      const promise = asyncFn(...args);
      cache.set(key, promise);
      
      // Clear cache after 5 minutes
      setTimeout(() => cache.delete(key), 5 * 60 * 1000);
      
      return promise;
    }
  );
};

// 6. Selector debugging utilities
const createDebugSelector = (selector, name) => {
  let callCount = 0;
  let lastResult = null;
  let lastInputs = null;
  
  return createSelector(
    selector.dependencies || [],
    (...args) => {
      callCount++;
      const start = performance.now();
      const result = selector.resultFunc(...args);
      const duration = performance.now() - start;
      
      console.group(`🔍 Selector: ${name}`);
      console.log(`Call #${callCount}`);
      console.log(`Duration: ${duration.toFixed(2)}ms`);
      console.log('Inputs:', args);
      console.log('Result:', result);
      console.log('Inputs changed:', JSON.stringify(args) !== JSON.stringify(lastInputs));
      console.log('Result changed:', JSON.stringify(result) !== JSON.stringify(lastResult));
      console.groupEnd();
      
      lastInputs = args;
      lastResult = result;
      
      return result;
    }
  );
};

// Usage
const debugGetFilteredUsers = createDebugSelector(getFilteredUsers, 'getFilteredUsers');
```

**Reselect Best Practices:**
```jsx
// 1. Selector organization
const selectors = {
  // Input selectors
  input: {
    getUsers: (state) => state.users.items,
    getFilters: (state) => state.ui.filters,
    getSorting: (state) => state.ui.sorting
  },
  
  // Computed selectors
  computed: {
    getFilteredUsers: createSelector(
      [selectors.input.getUsers, selectors.input.getFilters],
      (users, filters) => { /* implementation */ }
    ),
    
    getSortedUsers: createSelector(
      [selectors.computed.getFilteredUsers, selectors.input.getSorting],
      (users, sorting) => { /* implementation */ }
    )
  },
  
  // Statistics selectors
  stats: {
    getUserCount: createSelector(
      [selectors.input.getUsers],
      (users) => users.length
    ),
    
    getActiveUserCount: createSelector(
      [selectors.input.getUsers],
      (users) => users.filter(user => user.isActive).length
    )
  }
};

// 2. Selector testing
const testSelector = (selector, state, expectedResult) => {
  const result = selector(state);
  console.assert(
    JSON.stringify(result) === JSON.stringify(expectedResult),
    'Selector test failed',
    { result, expectedResult }
  );
};

// 3. Performance monitoring
const monitorSelector = (selector, name) => {
  let totalTime = 0;
  let callCount = 0;
  
  return createSelector(
    selector.dependencies,
    (...args) => {
      const start = performance.now();
      const result = selector.resultFunc(...args);
      const duration = performance.now() - start;
      
      totalTime += duration;
      callCount++;
      
      if (callCount % 100 === 0) {
        console.log(`📊 Selector ${name} stats:`, {
          calls: callCount,
          totalTime: totalTime.toFixed(2),
          averageTime: (totalTime / callCount).toFixed(2)
        });
      }
      
      return result;
    }
  );
};
```

**Interview Questions:**
1. What is Reselect and why is it useful?
2. How does memoization work in Reselect?
3. What are the performance benefits of using selectors?
4. How do you create parametric selectors?
5. What is the difference between input selectors and output selectors?
6. How do you test selectors?
7. When should you use Reselect vs regular selectors?
8. How do you debug selector performance issues?
9. What are some best practices for organizing selectors?
10. How do you handle complex data transformations with selectors?

---

## 🧭 WEEK 7–8: Routing and Performance Optimization

### 🔹 Day 29–30: React Router - DEEP DIVE

**Definition (English):**
React Router is the standard routing library for React applications that enables navigation between different components and views. It provides declarative routing, nested routes, route parameters, query strings, and programmatic navigation. React Router maintains the browser history and synchronizes the UI with the URL, enabling bookmarkable URLs and browser back/forward functionality.

**Hinglish Deep Explanation:**
React Router ek powerful library hai jo React applications mein navigation handle karti hai. Ye different pages/components ke beech switch karne ki facility deti hai bina page refresh kiye. Isme nested routes, dynamic routes, route parameters, aur programmatic navigation ki features hain. Browser ka history maintain karta hai aur URL ko UI ke saath sync rakhta hai.

**React Router Deep Understanding:**

**1. Basic Router Setup and Configuration:**
```jsx
import {
  BrowserRouter as Router,
  Routes,
  Route,
  Link,
  NavLink,
  Navigate,
  useNavigate,
  useLocation,
  useParams,
  useSearchParams,
  Outlet
} from 'react-router-dom';

// App with basic routing
function App() {
  return (
    <Router>
      <div className="app">
        <Navigation />
        <main className="main-content">
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/about" element={<About />} />
            <Route path="/products" element={<Products />} />
            <Route path="/products/:id" element={<ProductDetail />} />
            <Route path="/user/*" element={<UserRoutes />} />
            <Route path="/admin" element={<ProtectedRoute><Admin /></ProtectedRoute>} />
            <Route path="/login" element={<Login />} />
            <Route path="/404" element={<NotFound />} />
            <Route path="*" element={<Navigate to="/404" replace />} />
          </Routes>
        </main>
      </div>
    </Router>
  );
}

// Navigation component with active links
function Navigation() {
  const location = useLocation();
  
  return (
    <nav className="navigation">
      <div className="nav-brand">
        <Link to="/">MyApp</Link>
      </div>
      
      <ul className="nav-links">
        <li>
          <NavLink 
            to="/" 
            className={({ isActive }) => isActive ? 'nav-link active' : 'nav-link'}
          >
            Home
          </NavLink>
        </li>
        <li>
          <NavLink 
            to="/about"
            className={({ isActive }) => isActive ? 'nav-link active' : 'nav-link'}
          >
            About
          </NavLink>
        </li>
        <li>
          <NavLink 
            to="/products"
            className={({ isActive }) => isActive ? 'nav-link active' : 'nav-link'}
          >
            Products
          </NavLink>
        </li>
        <li>
          <NavLink 
            to="/user/profile"
            className={({ isActive }) => isActive ? 'nav-link active' : 'nav-link'}
          >
            Profile
          </NavLink>
        </li>
      </ul>
      
      <div className="nav-actions">
        <span className="current-path">Current: {location.pathname}</span>
      </div>
    </nav>
  );
}

// Home component
function Home() {
  const navigate = useNavigate();
  
  const handleGetStarted = () => {
    navigate('/products', { 
      state: { from: 'home-cta' },
      replace: false 
    });
  };
  
  return (
    <div className="home">
      <h1>Welcome to MyApp</h1>
      <p>This is the home page with React Router navigation.</p>
      <button onClick={handleGetStarted} className="cta-button">
        Get Started
      </button>
    </div>
  );
}

// Products component with search and filtering
function Products() {
  const [searchParams, setSearchParams] = useSearchParams();
  const location = useLocation();
  const navigate = useNavigate();
  
  const category = searchParams.get('category') || 'all';
  const search = searchParams.get('search') || '';
  const page = parseInt(searchParams.get('page')) || 1;
  
  const products = [
    { id: 1, name: 'Laptop', category: 'electronics', price: 50000 },
    { id: 2, name: 'Book', category: 'education', price: 500 },
    { id: 3, name: 'Phone', category: 'electronics', price: 25000 },
    { id: 4, name: 'Shirt', category: 'clothing', price: 1000 }
  ];
  
  const filteredProducts = products.filter(product => {
    const matchesCategory = category === 'all' || product.category === category;
    const matchesSearch = product.name.toLowerCase().includes(search.toLowerCase());
    return matchesCategory && matchesSearch;
  });
  
  const handleCategoryChange = (newCategory) => {
    setSearchParams(prev => {
      const newParams = new URLSearchParams(prev);
      if (newCategory === 'all') {
        newParams.delete('category');
      } else {
        newParams.set('category', newCategory);
      }
      newParams.delete('page'); // Reset page when changing category
      return newParams;
    });
  };
  
  const handleSearchChange = (newSearch) => {
    setSearchParams(prev => {
      const newParams = new URLSearchParams(prev);
      if (newSearch) {
        newParams.set('search', newSearch);
      } else {
        newParams.delete('search');
      }
      newParams.delete('page'); // Reset page when searching
      return newParams;
    });
  };
  
  const handlePageChange = (newPage) => {
    setSearchParams(prev => {
      const newParams = new URLSearchParams(prev);
      newParams.set('page', newPage.toString());
      return newParams;
    });
  };
  
  return (
    <div className="products">
      <h1>Products</h1>
      
      {/* Came from home CTA */}
      {location.state?.from === 'home-cta' && (
        <div className="welcome-message">
          Welcome! You came from the home page. Check out our products below.
        </div>
      )}
      
      {/* Filters */}
      <div className="filters">
        <div className="filter-group">
          <label>Category:</label>
          <select value={category} onChange={(e) => handleCategoryChange(e.target.value)}>
            <option value="all">All Categories</option>
            <option value="electronics">Electronics</option>
            <option value="education">Education</option>
            <option value="clothing">Clothing</option>
          </select>
        </div>
        
        <div className="filter-group">
          <label>Search:</label>
          <input
            type="text"
            value={search}
            onChange={(e) => handleSearchChange(e.target.value)}
            placeholder="Search products..."
          />
        </div>
      </div>
      
      {/* Products grid */}
      <div className="products-grid">
        {filteredProducts.map(product => (
          <div key={product.id} className="product-card">
            <h3>{product.name}</h3>
            <p>Category: {product.category}</p>
            <p>Price: ₹{product.price.toLocaleString()}</p>
            <Link 
              to={`/products/${product.id}`}
              state={{ product }}
              className="view-details-link"
            >
              View Details
            </Link>
          </div>
        ))}
      </div>
      
      {/* Pagination */}
      <div className="pagination">
        <button 
          onClick={() => handlePageChange(page - 1)}
          disabled={page <= 1}
        >
          Previous
        </button>
        <span>Page {page}</span>
        <button 
          onClick={() => handlePageChange(page + 1)}
          disabled={filteredProducts.length < 10}
        >
          Next
        </button>
      </div>
      
      {/* Current URL info */}
      <div className="url-info">
        <h3>Current URL Parameters:</h3>
        <pre>{JSON.stringify(Object.fromEntries(searchParams), null, 2)}</pre>
      </div>
    </div>
  );
}

// Product detail with dynamic routing
function ProductDetail() {
  const { id } = useParams();
  const location = useLocation();
  const navigate = useNavigate();
  
  // Get product from location state or fetch by ID
  const product = location.state?.product || {
    id: parseInt(id),
    name: `Product ${id}`,
    category: 'unknown',
    price: 0
  };
  
  const handleGoBack = () => {
    navigate(-1); // Go back in history
  };
  
  const handleGoToProducts = () => {
    navigate('/products', { replace: true });
  };
  
  return (
    <div className="product-detail">
      <div className="breadcrumb">
        <Link to="/">Home</Link> &gt; 
        <Link to="/products">Products</Link> &gt; 
        <span>{product.name}</span>
      </div>
      
      <h1>{product.name}</h1>
      <p>Product ID: {id}</p>
      <p>Category: {product.category}</p>
      <p>Price: ₹{product.price.toLocaleString()}</p>
      
      <div className="actions">
        <button onClick={handleGoBack}>Go Back</button>
        <button onClick={handleGoToProducts}>All Products</button>
      </div>
      
      {/* Related products */}
      <div className="related-products">
        <h3>Related Products</h3>
        <div className="related-grid">
          {[1, 2, 3].map(relatedId => (
            <Link 
              key={relatedId}
              to={`/products/${parseInt(id) + relatedId}`}
              className="related-product"
            >
              Related Product {parseInt(id) + relatedId}
            </Link>
          ))}
        </div>
      </div>
    </div>
  );
}
```

**Example 1: Nested Routes and Layout Components**
```jsx
// User routes with nested routing
function UserRoutes() {
  return (
    <div className="user-layout">
      <UserSidebar />
      <div className="user-content">
        <Routes>
          <Route index element={<UserDashboard />} />
          <Route path="profile" element={<UserProfile />} />
          <Route path="settings" element={<UserSettings />} />
          <Route path="orders" element={<UserOrders />} />
          <Route path="orders/:orderId" element={<OrderDetail />} />
          <Route path="notifications" element={<UserNotifications />} />
          <Route path="*" element={<Navigate to="/user" replace />} />
        </Routes>
      </div>
    </div>
  );
}

function UserSidebar() {
  const location = useLocation();
  
  const menuItems = [
    { path: '/user', label: 'Dashboard', icon: '📊' },
    { path: '/user/profile', label: 'Profile', icon: '👤' },
    { path: '/user/settings', label: 'Settings', icon: '⚙️' },
    { path: '/user/orders', label: 'Orders', icon: '📦' },
    { path: '/user/notifications', label: 'Notifications', icon: '🔔' }
  ];
  
  return (
    <aside className="user-sidebar">
      <h3>User Menu</h3>
      <nav>
        {menuItems.map(item => (
          <NavLink
            key={item.path}
            to={item.path}
            className={({ isActive }) => 
              `sidebar-link ${isActive ? 'active' : ''}`
            }
            end={item.path === '/user'}
          >
            <span className="icon">{item.icon}</span>
            <span className="label">{item.label}</span>
          </NavLink>
        ))}
      </nav>
    </aside>
  );
}

function UserDashboard() {
  const navigate = useNavigate();
  
  const quickActions = [
    { label: 'View Profile', path: '/user/profile' },
    { label: 'Recent Orders', path: '/user/orders' },
    { label: 'Account Settings', path: '/user/settings' }
  ];
  
  return (
    <div className="user-dashboard">
      <h2>Dashboard</h2>
      <p>Welcome to your user dashboard!</p>
      
      <div className="quick-actions">
        <h3>Quick Actions</h3>
        <div className="actions-grid">
          {quickActions.map(action => (
            <button
              key={action.path}
              onClick={() => navigate(action.path)}
              className="action-button"
            >
              {action.label}
            </button>
          ))}
        </div>
      </div>
      
      <div className="recent-activity">
        <h3>Recent Activity</h3>
        <ul>
          <li>Logged in from new device</li>
          <li>Updated profile information</li>
          <li>Placed order #12345</li>
        </ul>
      </div>
    </div>
  );
}

function UserOrders() {
  const navigate = useNavigate();
  
  const orders = [
    { id: '12345', date: '2024-01-15', status: 'delivered', total: 2500 },
    { id: '12346', date: '2024-01-20', status: 'shipped', total: 1800 },
    { id: '12347', date: '2024-01-25', status: 'processing', total: 3200 }
  ];
  
  return (
    <div className="user-orders">
      <h2>Your Orders</h2>
      
      <div className="orders-list">
        {orders.map(order => (
          <div key={order.id} className="order-card">
            <div className="order-header">
              <h3>Order #{order.id}</h3>
              <span className={`status ${order.status}`}>{order.status}</span>
            </div>
            <div className="order-details">
              <p>Date: {order.date}</p>
              <p>Total: ₹{order.total.toLocaleString()}</p>
            </div>
            <div className="order-actions">
              <button 
                onClick={() => navigate(`/user/orders/${order.id}`)}
                className="view-details-btn"
              >
                View Details
              </button>
            </div>
          </div>
        ))}
      </div>
    </div>
  );
}

function OrderDetail() {
  const { orderId } = useParams();
  const navigate = useNavigate();
  
  const order = {
    id: orderId,
    date: '2024-01-15',
    status: 'delivered',
    items: [
      { id: 1, name: 'Laptop', quantity: 1, price: 50000 },
      { id: 2, name: 'Mouse', quantity: 2, price: 1000 }
    ],
    shipping: {
      address: '123 Main St, City, State 12345',
      method: 'Standard Delivery',
      cost: 200
    }
  };
  
  const subtotal = order.items.reduce((sum, item) => sum + (item.price * item.quantity), 0);
  const total = subtotal + order.shipping.cost;
  
  return (
    <div className="order-detail">
      <div className="order-header">
        <button onClick={() => navigate('/user/orders')} className="back-btn">
          ← Back to Orders
        </button>
        <h2>Order #{orderId}</h2>
      </div>
      
      <div className="order-info">
        <div className="order-status">
          <h3>Status: <span className={`status ${order.status}`}>{order.status}</span></h3>
          <p>Order Date: {order.date}</p>
        </div>
        
        <div className="order-items">
          <h3>Items</h3>
          {order.items.map(item => (
            <div key={item.id} className="order-item">
              <span className="item-name">{item.name}</span>
              <span className="item-quantity">Qty: {item.quantity}</span>
              <span className="item-price">₹{(item.price * item.quantity).toLocaleString()}</span>
            </div>
          ))}
        </div>
        
        <div className="order-summary">
          <h3>Order Summary</h3>
          <div className="summary-line">
            <span>Subtotal:</span>
            <span>₹{subtotal.toLocaleString()}</span>
          </div>
          <div className="summary-line">
            <span>Shipping:</span>
            <span>₹{order.shipping.cost.toLocaleString()}</span>
          </div>
          <div className="summary-line total">
            <span>Total:</span>
            <span>₹{total.toLocaleString()}</span>
          </div>
        </div>
        
        <div className="shipping-info">
          <h3>Shipping Information</h3>
          <p><strong>Address:</strong> {order.shipping.address}</p>
          <p><strong>Method:</strong> {order.shipping.method}</p>
        </div>
      </div>
    </div>
  );
}
```

**Example 2: Protected Routes and Authentication**
```jsx
// Authentication context
const AuthContext = createContext();

function AuthProvider({ children }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  
  useEffect(() => {
    // Check for stored auth token
    const token = localStorage.getItem('authToken');
    if (token) {
      // Validate token and get user info
      validateToken(token).then(userData => {
        setUser(userData);
        setLoading(false);
      }).catch(() => {
        localStorage.removeItem('authToken');
        setLoading(false);
      });
    } else {
      setLoading(false);
    }
  }, []);
  
  const login = async (credentials) => {
    setLoading(true);
    try {
      const response = await fetch('/api/auth/login', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(credentials)
      });
      
      if (!response.ok) throw new Error('Login failed');
      
      const { user, token } = await response.json();
      localStorage.setItem('authToken', token);
      setUser(user);
      return user;
    } catch (error) {
      throw error;
    } finally {
      setLoading(false);
    }
  };
  
  const logout = () => {
    localStorage.removeItem('authToken');
    setUser(null);
  };
  
  const value = {
    user,
    loading,
    login,
    logout,
    isAuthenticated: !!user,
    isAdmin: user?.role === 'admin'
  };
  
  return (
    <AuthContext.Provider value={value}>
      {children}
    </AuthContext.Provider>
  );
}

function useAuth() {
  const context = useContext(AuthContext);
  if (!context) {
    throw new Error('useAuth must be used within AuthProvider');
  }
  return context;
}

// Protected route component
function ProtectedRoute({ children, requireAdmin = false }) {
  const { user, loading, isAuthenticated, isAdmin } = useAuth();
  const location = useLocation();
  
  if (loading) {
    return <div className="loading">Checking authentication...</div>;
  }
  
  if (!isAuthenticated) {
    return <Navigate to="/login" state={{ from: location }} replace />;
  }
  
  if (requireAdmin && !isAdmin) {
    return <Navigate to="/unauthorized" replace />;
  }
  
  return children;
}

// Login component with redirect
function Login() {
  const [credentials, setCredentials] = useState({ email: '', password: '' });
  const [error, setError] = useState('');
  const [loading, setLoading] = useState(false);
  
  const { login, isAuthenticated } = useAuth();
  const navigate = useNavigate();
  const location = useLocation();
  
  const from = location.state?.from?.pathname || '/';
  
  // Redirect if already authenticated
  useEffect(() => {
    if (isAuthenticated) {
      navigate(from, { replace: true });
    }
  }, [isAuthenticated, navigate, from]);
  
  const handleSubmit = async (e) => {
    e.preventDefault();
    setLoading(true);
    setError('');
    
    try {
      await login(credentials);
      navigate(from, { replace: true });
    } catch (error) {
      setError(error.message);
    } finally {
      setLoading(false);
    }
  };
  
  return (
    <div className="login-page">
      <div className="login-form">
        <h2>Login</h2>
        
        {location.state?.from && (
          <div className="redirect-notice">
            Please log in to access {location.state.from.pathname}
          </div>
        )}
        
        {error && <div className="error-message">{error}</div>}
        
        <form onSubmit={handleSubmit}>
          <div className="form-group">
            <input
              type="email"
              placeholder="Email"
              value={credentials.email}
              onChange={(e) => setCredentials(prev => ({ ...prev, email: e.target.value }))}
              required
            />
          </div>
          
          <div className="form-group">
            <input
              type="password"
              placeholder="Password"
              value={credentials.password}
              onChange={(e) => setCredentials(prev => ({ ...prev, password: e.target.value }))}
              required
            />
          </div>
          
          <button type="submit" disabled={loading} className="login-btn">
            {loading ? 'Logging in...' : 'Login'}
          </button>
        </form>
        
        <div className="login-help">
          <p>Demo credentials:</p>
          <p>User: user@example.com / password</p>
          <p>Admin: admin@example.com / password</p>
        </div>
      </div>
    </div>
  );
}

// Admin component (protected)
function Admin() {
  const { user, logout } = useAuth();
  const navigate = useNavigate();
  
  const handleLogout = () => {
    logout();
    navigate('/');
  };
  
  return (
    <div className="admin-page">
      <div className="admin-header">
        <h2>Admin Dashboard</h2>
        <div className="admin-user-info">
          Welcome, {user.name}
          <button onClick={handleLogout} className="logout-btn">Logout</button>
        </div>
      </div>
      
      <div className="admin-content">
        <div className="admin-stats">
          <div className="stat-card">
            <h3>Total Users</h3>
            <p className="stat-number">1,234</p>
          </div>
          <div className="stat-card">
            <h3>Total Orders</h3>
            <p className="stat-number">5,678</p>
          </div>
          <div className="stat-card">
            <h3>Revenue</h3>
            <p className="stat-number">₹12,34,567</p>
          </div>
        </div>
        
        <div className="admin-actions">
          <h3>Quick Actions</h3>
          <button className="admin-action-btn">Manage Users</button>
          <button className="admin-action-btn">View Reports</button>
          <button className="admin-action-btn">System Settings</button>
        </div>
      </div>
    </div>
  );
}

// Unauthorized page
function Unauthorized() {
  const navigate = useNavigate();
  
  return (
    <div className="unauthorized-page">
      <h2>Access Denied</h2>
      <p>You don't have permission to access this page.</p>
      <button onClick={() => navigate('/')} className="go-home-btn">
        Go Home
      </button>
    </div>
  );
}

// Main app with authentication
function AppWithAuth() {
  return (
    <AuthProvider>
      <Router>
        <div className="app">
          <Navigation />
          <main className="main-content">
            <Routes>
              <Route path="/" element={<Home />} />
              <Route path="/about" element={<About />} />
              <Route path="/products" element={<Products />} />
              <Route path="/products/:id" element={<ProductDetail />} />
              <Route path="/login" element={<Login />} />
              <Route path="/unauthorized" element={<Unauthorized />} />
              
              {/* Protected user routes */}
              <Route path="/user/*" element={
                <ProtectedRoute>
                  <UserRoutes />
                </ProtectedRoute>
              } />
              
              {/* Admin only routes */}
              <Route path="/admin" element={
                <ProtectedRoute requireAdmin>
                  <Admin />
                </ProtectedRoute>
              } />
              
              <Route path="/404" element={<NotFound />} />
              <Route path="*" element={<Navigate to="/404" replace />} />
            </Routes>
          </main>
        </div>
      </Router>
    </AuthProvider>
  );
}
```

**Example 3: Advanced Router Features**
```jsx
// Route-based code splitting with lazy loading
const LazyHome = lazy(() => import('./pages/Home'));
const LazyProducts = lazy(() => import('./pages/Products'));
const LazyAdmin = lazy(() => import('./pages/Admin'));

// Loading component
function RouteLoading() {
  return (
    <div className="route-loading">
      <div className="spinner"></div>
      <p>Loading page...</p>
    </div>
  );
}

// Error boundary for route errors
class RouteErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false, error: null };
  }
  
  static getDerivedStateFromError(error) {
    return { hasError: true, error };
  }
  
  componentDidCatch(error, errorInfo) {
    console.error('Route error:', error, errorInfo);
  }
  
  render() {
    if (this.state.hasError) {
      return (
        <div className="route-error">
          <h2>Something went wrong</h2>
          <p>{this.state.error?.message}</p>
          <button onClick={() => window.location.reload()}>
            Reload Page
          </button>
        </div>
      );
    }
    
    return this.props.children;
  }
}

// Custom hook for route analytics
function useRouteAnalytics() {
  const location = useLocation();
  
  useEffect(() => {
    // Track page view
    if (typeof window !== 'undefined' && window.gtag) {
      window.gtag('config', 'GA_MEASUREMENT_ID', {
        page_path: location.pathname + location.search
      });
    }
    
    // Custom analytics
    console.log('Page view:', {
      path: location.pathname,
      search: location.search,
      timestamp: new Date().toISOString()
    });
  }, [location]);
}

// Route transition animations
function AnimatedRoutes() {
  const location = useLocation();
  
  return (
    <AnimatePresence mode="wait">
      <motion.div
        key={location.pathname}
        initial={{ opacity: 0, x: 20 }}
        animate={{ opacity: 1, x: 0 }}
        exit={{ opacity: 0, x: -20 }}
        transition={{ duration: 0.3 }}
      >
        <Routes location={location}>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/products" element={<Products />} />
        </Routes>
      </motion.div>
    </AnimatePresence>
  );
}

// Advanced app with all features
function AdvancedRouterApp() {
  useRouteAnalytics();
  
  return (
    <Router>
      <div className="app">
        <Navigation />
        <main className="main-content">
          <RouteErrorBoundary>
            <Suspense fallback={<RouteLoading />}>
              <Routes>
                <Route path="/" element={<LazyHome />} />
                <Route path="/products" element={<LazyProducts />} />
                <Route path="/admin" element={
                  <ProtectedRoute requireAdmin>
                    <LazyAdmin />
                  </ProtectedRoute>
                } />
                <Route path="*" element={<NotFound />} />
              </Routes>
            </Suspense>
          </RouteErrorBoundary>
        </main>
      </div>
    </Router>
  );
}
```

**Router Best Practices:**
```jsx
// 1. Route configuration object
const routeConfig = [
  {
    path: '/',
    element: Home,
    exact: true
  },
  {
    path: '/products',
    element: Products,
    children: [
      {
        path: ':id',
        element: ProductDetail
      }
    ]
  },
  {
    path: '/admin',
    element: Admin,
    protected: true,
    requireAdmin: true
  }
];

// 2. Route generator
function generateRoutes(routes) {
  return routes.map(route => {
    let element = <route.element />;
    
    if (route.protected) {
      element = (
        <ProtectedRoute requireAdmin={route.requireAdmin}>
          {element}
        </ProtectedRoute>
      );
    }
    
    return (
      <Route
        key={route.path}
        path={route.path}
        element={element}
      >
        {route.children && generateRoutes(route.children)}
      </Route>
    );
  });
}

// 3. Custom hooks for common patterns
function useQueryParams() {
  const [searchParams, setSearchParams] = useSearchParams();
  
  const getParam = (key, defaultValue = null) => {
    return searchParams.get(key) || defaultValue;
  };
  
  const setParam = (key, value) => {
    setSearchParams(prev => {
      const newParams = new URLSearchParams(prev);
      if (value === null || value === undefined) {
        newParams.delete(key);
      } else {
        newParams.set(key, value);
      }
      return newParams;
    });
  };
  
  return { getParam, setParam, searchParams };
}

function useBreadcrumbs() {
  const location = useLocation();
  
  const breadcrumbs = useMemo(() => {
    const pathnames = location.pathname.split('/').filter(x => x);
    
    return pathnames.map((pathname, index) => {
      const to = `/${pathnames.slice(0, index + 1).join('/')}`;
      return {
        name: pathname.charAt(0).toUpperCase() + pathname.slice(1),
        path: to,
        isLast: index === pathnames.length - 1
      };
    });
  }, [location.pathname]);
  
  return breadcrumbs;
}
```

**Interview Questions:**
1. What is React Router and why do we need it?
2. What's the difference between BrowserRouter and HashRouter?
3. How do you handle dynamic routes with parameters?
4. What are nested routes and how do you implement them?
5. How do you implement protected routes?
6. What's the difference between Link and NavLink?
7. How do you handle programmatic navigation?
8. What are query parameters and how do you work with them?
9. How do you implement route-based code splitting?
10. What are some best practices for organizing routes?

---### 🔹 
Day 31–32: Code Splitting - DEEP DIVE

**Definition (English):**
Code splitting is a technique that allows you to split your JavaScript bundle into smaller chunks that can be loaded on demand. This improves initial load time by only loading the code that's immediately needed. React provides built-in support for code splitting through dynamic imports, React.lazy(), and Suspense components.

**Hinglish Deep Explanation:**
Code splitting ek optimization technique hai jo large JavaScript bundles ko chhote pieces mein tod deti hai. Isse initial page load time kam ho jaata hai kyunki sirf zaruri code pehle load hota hai, baaki code jab chahiye tab load hota hai. React mein ye React.lazy() aur Suspense ke through easily implement kar sakte hain.

**Code Splitting Deep Understanding:**

**1. Basic Code Splitting with React.lazy():**
```jsx
import React, { Suspense, lazy, useState } from 'react';

// Lazy load components
const LazyDashboard = lazy(() => import('./components/Dashboard'));
const LazyProfile = lazy(() => import('./components/Profile'));
const LazySettings = lazy(() => import('./components/Settings'));
const LazyAnalytics = lazy(() => import('./components/Analytics'));

// Loading component
function LoadingSpinner({ message = 'Loading...' }) {
  return (
    <div className="loading-container">
      <div className="spinner"></div>
      <p>{message}</p>
    </div>
  );
}

// Error boundary for lazy components
class LazyErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false, error: null };
  }
  
  static getDerivedStateFromError(error) {
    return { hasError: true, error };
  }
  
  componentDidCatch(error, errorInfo) {
    console.error('Lazy loading error:', error, errorInfo);
  }
  
  render() {
    if (this.state.hasError) {
      return (
        <div className="error-container">
          <h3>Failed to load component</h3>
          <p>{this.state.error?.message}</p>
          <button onClick={() => window.location.reload()}>
            Retry
          </button>
        </div>
      );
    }
    
    return this.props.children;
  }
}

// Main app with lazy loading
function CodeSplittingApp() {
  const [currentView, setCurrentView] = useState('dashboard');
  const [loadingStates, setLoadingStates] = useState({});
  
  const views = [
    { key: 'dashboard', label: 'Dashboard', component: LazyDashboard },
    { key: 'profile', label: 'Profile', component: LazyProfile },
    { key: 'settings', label: 'Settings', component: LazySettings },
    { key: 'analytics', label: 'Analytics', component: LazyAnalytics }
  ];
  
  const handleViewChange = (viewKey) => {
    setCurrentView(viewKey);
    setLoadingStates(prev => ({ ...prev, [viewKey]: true }));
    
    // Simulate loading time tracking
    setTimeout(() => {
      setLoadingStates(prev => ({ ...prev, [viewKey]: false }));
    }, 100);
  };
  
  const currentViewData = views.find(view => view.key === currentView);
  const CurrentComponent = currentViewData?.component;
  
  return (
    <div className="code-splitting-app">
      <nav className="app-nav">
        <h2>Code Splitting Demo</h2>
        <div className="nav-buttons">
          {views.map(view => (
            <button
              key={view.key}
              onClick={() => handleViewChange(view.key)}
              className={`nav-button ${currentView === view.key ? 'active' : ''}`}
              disabled={loadingStates[view.key]}
            >
              {loadingStates[view.key] ? 'Loading...' : view.label}
            </button>
          ))}
        </div>
      </nav>
      
      <main className="app-content">
        <LazyErrorBoundary>
          <Suspense fallback={<LoadingSpinner message={`Loading ${currentViewData?.label}...`} />}>
            {CurrentComponent && <CurrentComponent />}
          </Suspense>
        </LazyErrorBoundary>
      </main>
      
      {/* Bundle size info */}
      <div className="bundle-info">
        <h3>Bundle Information</h3>
        <p>Each component is loaded separately when needed</p>
        <p>Current view: {currentViewData?.label}</p>
      </div>
    </div>
  );
}

// Example lazy components
// Dashboard.jsx
function Dashboard() {
  const [data, setData] = useState(null);
  
  useEffect(() => {
    // Simulate data loading
    setTimeout(() => {
      setData({
        users: 1234,
        orders: 5678,
        revenue: 123456
      });
    }, 500);
  }, []);
  
  if (!data) {
    return <div>Loading dashboard data...</div>;
  }
  
  return (
    <div className="dashboard">
      <h2>Dashboard</h2>
      <div className="stats-grid">
        <div className="stat-card">
          <h3>Users</h3>
          <p className="stat-number">{data.users.toLocaleString()}</p>
        </div>
        <div className="stat-card">
          <h3>Orders</h3>
          <p className="stat-number">{data.orders.toLocaleString()}</p>
        </div>
        <div className="stat-card">
          <h3>Revenue</h3>
          <p className="stat-number">₹{data.revenue.toLocaleString()}</p>
        </div>
      </div>
    </div>
  );
}

// Profile.jsx
function Profile() {
  const [profile, setProfile] = useState({
    name: 'John Doe',
    email: 'john@example.com',
    avatar: '/default-avatar.png'
  });
  
  return (
    <div className="profile">
      <h2>User Profile</h2>
      <div className="profile-content">
        <div className="profile-avatar">
          <img src={profile.avatar} alt="Profile" />
        </div>
        <div className="profile-info">
          <h3>{profile.name}</h3>
          <p>{profile.email}</p>
          <button className="edit-profile-btn">Edit Profile</button>
        </div>
      </div>
    </div>
  );
}
```

**Example 1: Advanced Code Splitting Patterns**
```jsx
// 1. Conditional lazy loading
const ConditionalLazyComponent = lazy(() => {
  // Only load if user has premium access
  const userHasPremium = localStorage.getItem('userPremium') === 'true';
  
  if (userHasPremium) {
    return import('./PremiumFeatures');
  } else {
    return import('./BasicFeatures');
  }
});

// 2. Lazy loading with retry mechanism
function lazyWithRetry(importFunc, retries = 3) {
  return lazy(() => {
    return new Promise((resolve, reject) => {
      const attemptImport = (attempt) => {
        importFunc()
          .then(resolve)
          .catch((error) => {
            if (attempt < retries) {
              console.log(`Import failed, retrying... (${attempt + 1}/${retries})`);
              setTimeout(() => attemptImport(attempt + 1), 1000 * attempt);
            } else {
              reject(error);
            }
          });
      };
      
      attemptImport(0);
    });
  });
}

const RetryLazyComponent = lazyWithRetry(() => import('./HeavyComponent'));

// 3. Preloading components
function usePreloadComponent(importFunc) {
  const [preloaded, setPreloaded] = useState(false);
  
  const preload = useCallback(() => {
    if (!preloaded) {
      importFunc().then(() => {
        setPreloaded(true);
        console.log('Component preloaded');
      });
    }
  }, [importFunc, preloaded]);
  
  return { preload, preloaded };
}

function PreloadExample() {
  const { preload: preloadAnalytics } = usePreloadComponent(() => import('./Analytics'));
  
  return (
    <div>
      <button 
        onMouseEnter={preloadAnalytics} // Preload on hover
        onClick={() => setCurrentView('analytics')}
      >
        Analytics (Hover to preload)
      </button>
    </div>
  );
}

// 4. Route-based code splitting with React Router
import { Routes, Route } from 'react-router-dom';

const HomePage = lazy(() => import('./pages/Home'));
const ProductsPage = lazy(() => import('./pages/Products'));
const ProductDetailPage = lazy(() => import('./pages/ProductDetail'));
const CheckoutPage = lazy(() => import('./pages/Checkout'));
const AdminPage = lazy(() => import('./pages/Admin'));

function RouteSplittingApp() {
  return (
    <Router>
      <div className="app">
        <Navigation />
        <Suspense fallback={<PageLoader />}>
          <Routes>
            <Route path="/" element={<HomePage />} />
            <Route path="/products" element={<ProductsPage />} />
            <Route path="/products/:id" element={<ProductDetailPage />} />
            <Route path="/checkout" element={<CheckoutPage />} />
            <Route path="/admin/*" element={<AdminPage />} />
          </Routes>
        </Suspense>
      </div>
    </Router>
  );
}

// 5. Feature-based code splitting
const FeatureModules = {
  ecommerce: lazy(() => import('./features/Ecommerce')),
  analytics: lazy(() => import('./features/Analytics')),
  messaging: lazy(() => import('./features/Messaging')),
  fileManager: lazy(() => import('./features/FileManager'))
};

function FeatureBasedApp() {
  const [enabledFeatures, setEnabledFeatures] = useState(['ecommerce']);
  const [activeFeature, setActiveFeature] = useState('ecommerce');
  
  const loadFeature = (featureName) => {
    if (!enabledFeatures.includes(featureName)) {
      setEnabledFeatures(prev => [...prev, featureName]);
    }
    setActiveFeature(featureName);
  };
  
  const ActiveFeatureComponent = FeatureModules[activeFeature];
  
  return (
    <div className="feature-app">
      <div className="feature-nav">
        {Object.keys(FeatureModules).map(feature => (
          <button
            key={feature}
            onClick={() => loadFeature(feature)}
            className={`feature-btn ${activeFeature === feature ? 'active' : ''}`}
          >
            {feature.charAt(0).toUpperCase() + feature.slice(1)}
            {!enabledFeatures.includes(feature) && ' (Load)'}
          </button>
        ))}
      </div>
      
      <div className="feature-content">
        <Suspense fallback={<div>Loading {activeFeature} feature...</div>}>
          <ActiveFeatureComponent />
        </Suspense>
      </div>
    </div>
  );
}
```

**Example 2: Dynamic Imports and Module Loading**
```jsx
// 1. Dynamic utility loading
function useDynamicUtils() {
  const [utils, setUtils] = useState(null);
  const [loading, setLoading] = useState(false);
  
  const loadUtils = async (utilName) => {
    setLoading(true);
    try {
      let utilModule;
      
      switch (utilName) {
        case 'charts':
          utilModule = await import('./utils/chartUtils');
          break;
        case 'export':
          utilModule = await import('./utils/exportUtils');
          break;
        case 'validation':
          utilModule = await import('./utils/validationUtils');
          break;
        default:
          throw new Error(`Unknown utility: ${utilName}`);
      }
      
      setUtils(utilModule);
    } catch (error) {
      console.error('Failed to load utility:', error);
    } finally {
      setLoading(false);
    }
  };
  
  return { utils, loading, loadUtils };
}

// 2. Dynamic component loading based on data
function DynamicComponentLoader({ componentType, data }) {
  const [Component, setComponent] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    const loadComponent = async () => {
      setLoading(true);
      setError(null);
      
      try {
        let componentModule;
        
        switch (componentType) {
          case 'chart':
            componentModule = await import('./components/Chart');
            break;
          case 'table':
            componentModule = await import('./components/DataTable');
            break;
          case 'form':
            componentModule = await import('./components/DynamicForm');
            break;
          case 'map':
            componentModule = await import('./components/MapView');
            break;
          default:
            throw new Error(`Unknown component type: ${componentType}`);
        }
        
        setComponent(() => componentModule.default);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    };
    
    loadComponent();
  }, [componentType]);
  
  if (loading) return <div>Loading {componentType} component...</div>;
  if (error) return <div>Error loading component: {error}</div>;
  if (!Component) return null;
  
  return <Component data={data} />;
}

// 3. Progressive loading with skeleton screens
function ProgressiveLoader({ children, skeleton }) {
  const [loaded, setLoaded] = useState(false);
  
  useEffect(() => {
    // Simulate progressive loading
    const timer = setTimeout(() => setLoaded(true), 1000);
    return () => clearTimeout(timer);
  }, []);
  
  return (
    <div className="progressive-loader">
      {loaded ? children : skeleton}
    </div>
  );
}

function SkeletonCard() {
  return (
    <div className="skeleton-card">
      <div className="skeleton-header"></div>
      <div className="skeleton-content">
        <div className="skeleton-line"></div>
        <div className="skeleton-line short"></div>
      </div>
    </div>
  );
}

// Usage
function ProgressiveApp() {
  return (
    <div className="progressive-app">
      <ProgressiveLoader skeleton={<SkeletonCard />}>
        <Suspense fallback={<SkeletonCard />}>
          <LazyDashboard />
        </Suspense>
      </ProgressiveLoader>
    </div>
  );
}

// 4. Intelligent preloading based on user behavior
function useIntelligentPreloading() {
  const [preloadQueue, setPreloadQueue] = useState([]);
  const [preloadedModules, setPreloadedModules] = useState(new Set());
  
  const addToPreloadQueue = (importFunc, priority = 1) => {
    setPreloadQueue(prev => [...prev, { importFunc, priority }]);
  };
  
  const preloadNext = useCallback(async () => {
    if (preloadQueue.length === 0) return;
    
    // Sort by priority and preload highest priority first
    const sortedQueue = [...preloadQueue].sort((a, b) => b.priority - a.priority);
    const nextItem = sortedQueue[0];
    
    try {
      await nextItem.importFunc();
      setPreloadedModules(prev => new Set([...prev, nextItem.importFunc.toString()]));
      setPreloadQueue(prev => prev.filter(item => item !== nextItem));
    } catch (error) {
      console.error('Preload failed:', error);
    }
  }, [preloadQueue]);
  
  // Preload during idle time
  useEffect(() => {
    if ('requestIdleCallback' in window) {
      const idleCallback = window.requestIdleCallback(preloadNext);
      return () => window.cancelIdleCallback(idleCallback);
    } else {
      const timeout = setTimeout(preloadNext, 100);
      return () => clearTimeout(timeout);
    }
  }, [preloadNext]);
  
  return { addToPreloadQueue, preloadedModules };
}

// 5. Bundle analysis and optimization
function BundleAnalyzer() {
  const [bundleInfo, setBundleInfo] = useState(null);
  
  useEffect(() => {
    // Simulate bundle analysis
    const analyzeBundles = () => {
      const bundles = [
        { name: 'main', size: '245 KB', chunks: ['main', 'vendor'] },
        { name: 'dashboard', size: '89 KB', chunks: ['dashboard'] },
        { name: 'analytics', size: '156 KB', chunks: ['analytics', 'charts'] },
        { name: 'admin', size: '67 KB', chunks: ['admin'] }
      ];
      
      setBundleInfo(bundles);
    };
    
    analyzeBundles();
  }, []);
  
  if (!bundleInfo) return <div>Analyzing bundles...</div>;
  
  return (
    <div className="bundle-analyzer">
      <h3>Bundle Analysis</h3>
      <div className="bundle-list">
        {bundleInfo.map(bundle => (
          <div key={bundle.name} className="bundle-item">
            <h4>{bundle.name}</h4>
            <p>Size: {bundle.size}</p>
            <p>Chunks: {bundle.chunks.join(', ')}</p>
          </div>
        ))}
      </div>
      
      <div className="optimization-tips">
        <h4>Optimization Tips:</h4>
        <ul>
          <li>Consider splitting large chunks further</li>
          <li>Preload critical routes</li>
          <li>Use tree shaking for unused code</li>
          <li>Implement service worker caching</li>
        </ul>
      </div>
    </div>
  );
}
```

**Example 3: Advanced Loading States and Error Handling**
```jsx
// 1. Advanced loading states
function useLoadingState() {
  const [loadingStates, setLoadingStates] = useState({});
  
  const setLoading = (key, loading, message = '') => {
    setLoadingStates(prev => ({
      ...prev,
      [key]: loading ? { loading: true, message } : { loading: false }
    }));
  };
  
  const isLoading = (key) => loadingStates[key]?.loading || false;
  const getLoadingMessage = (key) => loadingStates[key]?.message || '';
  
  return { setLoading, isLoading, getLoadingMessage };
}

// 2. Smart error boundaries with retry
function SmartErrorBoundary({ children, fallback, onRetry }) {
  const [hasError, setHasError] = useState(false);
  const [error, setError] = useState(null);
  const [retryCount, setRetryCount] = useState(0);
  
  const retry = () => {
    setHasError(false);
    setError(null);
    setRetryCount(prev => prev + 1);
    onRetry?.();
  };
  
  useEffect(() => {
    if (hasError && retryCount < 3) {
      // Auto retry up to 3 times
      const timer = setTimeout(retry, 2000);
      return () => clearTimeout(timer);
    }
  }, [hasError, retryCount]);
  
  if (hasError) {
    return fallback ? fallback(error, retry, retryCount) : (
      <div className="error-boundary">
        <h3>Something went wrong</h3>
        <p>{error?.message}</p>
        <button onClick={retry} disabled={retryCount >= 3}>
          {retryCount >= 3 ? 'Max retries reached' : `Retry (${retryCount}/3)`}
        </button>
      </div>
    );
  }
  
  return children;
}

// 3. Comprehensive loading component
function ComprehensiveLoader({ 
  loading, 
  error, 
  retry, 
  progress, 
  message, 
  skeleton,
  children 
}) {
  if (error) {
    return (
      <div className="loader-error">
        <div className="error-icon">⚠️</div>
        <h3>Loading Failed</h3>
        <p>{error.message}</p>
        <button onClick={retry} className="retry-btn">
          Try Again
        </button>
      </div>
    );
  }
  
  if (loading) {
    return (
      <div className="comprehensive-loader">
        {skeleton || (
          <div className="loader-content">
            <div className="loader-spinner"></div>
            {progress !== undefined && (
              <div className="progress-bar">
                <div 
                  className="progress-fill" 
                  style={{ width: `${progress}%` }}
                ></div>
              </div>
            )}
            <p className="loader-message">{message || 'Loading...'}</p>
          </div>
        )}
      </div>
    );
  }
  
  return children;
}

// 4. Performance monitoring
function usePerformanceMonitoring() {
  const [metrics, setMetrics] = useState({});
  
  const startTiming = (key) => {
    setMetrics(prev => ({
      ...prev,
      [key]: { startTime: performance.now() }
    }));
  };
  
  const endTiming = (key) => {
    setMetrics(prev => {
      const metric = prev[key];
      if (metric) {
        const duration = performance.now() - metric.startTime;
        return {
          ...prev,
          [key]: { ...metric, duration, endTime: performance.now() }
        };
      }
      return prev;
    });
  };
  
  const getMetrics = () => metrics;
  
  return { startTiming, endTiming, getMetrics };
}

// 5. Complete code splitting solution
function CompleteCodeSplittingApp() {
  const { setLoading, isLoading, getLoadingMessage } = useLoadingState();
  const { startTiming, endTiming, getMetrics } = usePerformanceMonitoring();
  const [currentRoute, setCurrentRoute] = useState('home');
  
  const routes = {
    home: {
      component: lazy(() => {
        startTiming('home');
        return import('./pages/Home').then(module => {
          endTiming('home');
          return module;
        });
      }),
      preload: () => import('./pages/Home')
    },
    dashboard: {
      component: lazy(() => {
        startTiming('dashboard');
        return import('./pages/Dashboard').then(module => {
          endTiming('dashboard');
          return module;
        });
      }),
      preload: () => import('./pages/Dashboard')
    },
    analytics: {
      component: lazy(() => {
        startTiming('analytics');
        return import('./pages/Analytics').then(module => {
          endTiming('analytics');
          return module;
        });
      }),
      preload: () => import('./pages/Analytics')
    }
  };
  
  const handleRouteChange = (route) => {
    setLoading(route, true, `Loading ${route}...`);
    setCurrentRoute(route);
    
    // Simulate loading completion
    setTimeout(() => {
      setLoading(route, false);
    }, 100);
  };
  
  const handlePreload = (route) => {
    routes[route]?.preload();
  };
  
  const CurrentComponent = routes[currentRoute]?.component;
  
  return (
    <div className="complete-app">
      <nav className="app-navigation">
        {Object.keys(routes).map(route => (
          <button
            key={route}
            onClick={() => handleRouteChange(route)}
            onMouseEnter={() => handlePreload(route)}
            className={`nav-btn ${currentRoute === route ? 'active' : ''}`}
            disabled={isLoading(route)}
          >
            {route.charAt(0).toUpperCase() + route.slice(1)}
          </button>
        ))}
      </nav>
      
      <main className="app-main">
        <SmartErrorBoundary
          fallback={(error, retry, retryCount) => (
            <div className="route-error">
              <h3>Failed to load page</h3>
              <p>{error.message}</p>
              <button onClick={retry}>
                Retry ({retryCount}/3)
              </button>
            </div>
          )}
        >
          <Suspense 
            fallback={
              <ComprehensiveLoader
                loading={true}
                message={getLoadingMessage(currentRoute)}
                skeleton={<div className="page-skeleton">Loading page...</div>}
              />
            }
          >
            {CurrentComponent && <CurrentComponent />}
          </Suspense>
        </SmartErrorBoundary>
      </main>
      
      <div className="performance-metrics">
        <h4>Performance Metrics</h4>
        <pre>{JSON.stringify(getMetrics(), null, 2)}</pre>
      </div>
    </div>
  );
}
```

**Code Splitting Best Practices:**
```jsx
// 1. Webpack bundle analysis
// Add to package.json scripts:
// "analyze": "npm run build && npx webpack-bundle-analyzer build/static/js/*.js"

// 2. Preloading strategies
const preloadStrategies = {
  // Preload on hover
  onHover: (importFunc) => {
    return { onMouseEnter: () => importFunc() };
  },
  
  // Preload on viewport
  onViewport: (importFunc) => {
    const ref = useRef();
    
    useEffect(() => {
      const observer = new IntersectionObserver(([entry]) => {
        if (entry.isIntersecting) {
          importFunc();
          observer.disconnect();
        }
      });
      
      if (ref.current) observer.observe(ref.current);
      
      return () => observer.disconnect();
    }, []);
    
    return { ref };
  },
  
  // Preload after delay
  afterDelay: (importFunc, delay = 2000) => {
    useEffect(() => {
      const timer = setTimeout(importFunc, delay);
      return () => clearTimeout(timer);
    }, []);
  }
};

// 3. Error handling patterns
const errorHandlingPatterns = {
  // Retry with exponential backoff
  retryWithBackoff: (importFunc, maxRetries = 3) => {
    return lazy(() => {
      let retries = 0;
      
      const attemptImport = () => {
        return importFunc().catch(error => {
          if (retries < maxRetries) {
            retries++;
            const delay = Math.pow(2, retries) * 1000;
            return new Promise(resolve => {
              setTimeout(() => resolve(attemptImport()), delay);
            });
          }
          throw error;
        });
      };
      
      return attemptImport();
    });
  },
  
  // Fallback to different component
  withFallback: (primaryImport, fallbackImport) => {
    return lazy(() => {
      return primaryImport().catch(() => fallbackImport());
    });
  }
};
```

**Interview Questions:**
1. What is code splitting and why is it important?
2. How does React.lazy() work internally?
3. What is the role of Suspense in code splitting?
4. How do you implement route-based code splitting?
5. What are the different strategies for preloading components?
6. How do you handle errors in lazy-loaded components?
7. What tools can you use to analyze bundle sizes?
8. How do you optimize code splitting for better performance?
9. What are the trade-offs of code splitting?
10. How do you test lazy-loaded components?

---#
## 🔹 Day 33–34: Performance Optimization - DEEP DIVE

**Definition (English):**
Performance optimization in React involves techniques to make applications faster, more responsive, and efficient. This includes preventing unnecessary re-renders, optimizing expensive computations, managing memory usage, and improving user experience through techniques like memoization, virtualization, and efficient state management.

**Hinglish Deep Explanation:**
React performance optimization ka matlab hai app ko fast aur smooth banana. Isme unnecessary re-renders rokna, expensive calculations optimize karna, memory efficiently use karna, aur user experience improve karna shamil hai. Main techniques hain memoization (React.memo, useMemo, useCallback), virtualization, aur efficient state management.

**Performance Optimization Deep Understanding:**

**1. React.memo and Component Memoization:**
```jsx
import React, { memo, useState, useCallback, useMemo } from 'react';

// Basic React.memo usage
const ExpensiveComponent = memo(function ExpensiveComponent({ data, onUpdate }) {
  console.log('ExpensiveComponent rendered');
  
  // Simulate expensive calculation
  const processedData = useMemo(() => {
    console.log('Processing data...');
    return data.map(item => ({
      ...item,
      processed: true,
      timestamp: Date.now()
    }));
  }, [data]);
  
  return (
    <div className="expensive-component">
      <h3>Expensive Component</h3>
      <p>Items: {processedData.length}</p>
      <button onClick={() => onUpdate(processedData)}>Update</button>
    </div>
  );
});

// Custom comparison function for React.memo
const SmartComponent = memo(function SmartComponent({ user, settings }) {
  console.log('SmartComponent rendered');
  
  return (
    <div>
      <h3>{user.name}</h3>
      <p>Theme: {settings.theme}</p>
    </div>
  );
}, (prevProps, nextProps) => {
  // Custom comparison - only re-render if user.name or settings.theme changes
  return (
    prevProps.user.name === nextProps.user.name &&
    prevProps.settings.theme === nextProps.settings.theme
  );
});

// Performance comparison demo
function PerformanceDemo() {
  const [count, setCount] = useState(0);
  const [users, setUsers] = useState([
    { id: 1, name: 'John', age: 25 },
    { id: 2, name: 'Jane', age: 30 }
  ]);
  const [settings, setSettings] = useState({ theme: 'light', lang: 'en' });
  
  // This will cause unnecessary re-renders without memoization
  const handleUpdate = (data) => {
    console.log('Data updated:', data);
  };
  
  // Memoized callback
  const memoizedUpdate = useCallback((data) => {
    console.log('Memoized update:', data);
  }, []);
  
  return (
    <div className="performance-demo">
      <h2>Performance Optimization Demo</h2>
      
      <div className="controls">
        <button onClick={() => setCount(count + 1)}>
          Count: {count}
        </button>
        <button onClick={() => setSettings(prev => ({ 
          ...prev, 
          theme: prev.theme === 'light' ? 'dark' : 'light' 
        }))}>
          Toggle Theme
        </button>
      </div>
      
      {/* Without memoization - re-renders on every count change */}
      <div className="section">
        <h3>Without Optimization</h3>
        <ExpensiveComponent data={users} onUpdate={handleUpdate} />
      </div>
      
      {/* With memoization - only re-renders when data or callback changes */}
      <div className="section">
        <h3>With Optimization</h3>
        <ExpensiveComponent data={users} onUpdate={memoizedUpdate} />
      </div>
      
      {/* Smart component with custom comparison */}
      <div className="section">
        <h3>Smart Component</h3>
        <SmartComponent user={users[0]} settings={settings} />
      </div>
    </div>
  );
}
```

**Example 1: Advanced Memoization Patterns:**
```jsx
// 1. useMemo for expensive calculations
function DataProcessor({ rawData, filters, sortConfig }) {
  // Expensive filtering operation
  const filteredData = useMemo(() => {
    console.log('🔄 Filtering data...');
    return rawData.filter(item => {
      return Object.entries(filters).every(([key, value]) => {
        if (!value) return true;
        return item[key]?.toString().toLowerCase().includes(value.toLowerCase());
      });
    });
  }, [rawData, filters]);
  
  // Expensive sorting operation
  const sortedData = useMemo(() => {
    console.log('📊 Sorting data...');
    if (!sortConfig.field) return filteredData;
    
    return [...filteredData].sort((a, b) => {
      const aValue = a[sortConfig.field];
      const bValue = b[sortConfig.field];
      
      if (sortConfig.direction === 'asc') {
        return aValue > bValue ? 1 : -1;
      } else {
        return aValue < bValue ? 1 : -1;
      }
    });
  }, [filteredData, sortConfig]);
  
  // Expensive aggregation
  const statistics = useMemo(() => {
    console.log('📈 Calculating statistics...');
    return {
      total: sortedData.length,
      average: sortedData.reduce((sum, item) => sum + (item.value || 0), 0) / sortedData.length,
      max: Math.max(...sortedData.map(item => item.value || 0)),
      min: Math.min(...sortedData.map(item => item.value || 0))
    };
  }, [sortedData]);
  
  return (
    <div className="data-processor">
      <div className="statistics">
        <h3>Statistics</h3>
        <p>Total: {statistics.total}</p>
        <p>Average: {statistics.average.toFixed(2)}</p>
        <p>Max: {statistics.max}</p>
        <p>Min: {statistics.min}</p>
      </div>
      
      <div className="data-list">
        {sortedData.map(item => (
          <div key={item.id} className="data-item">
            <span>{item.name}</span>
            <span>{item.value}</span>
          </div>
        ))}
      </div>
    </div>
  );
}

// 2. useCallback for event handlers
function OptimizedForm({ onSubmit, onValidate }) {
  const [formData, setFormData] = useState({ name: '', email: '', message: '' });
  const [errors, setErrors] = useState({});
  
  // Memoized field update handler
  const handleFieldChange = useCallback((field) => {
    return (event) => {
      const value = event.target.value;
      setFormData(prev => ({ ...prev, [field]: value }));
      
      // Clear error when user starts typing
      if (errors[field]) {
        setErrors(prev => ({ ...prev, [field]: null }));
      }
    };
  }, [errors]);
  
  // Memoized validation
  const validateForm = useCallback(() => {
    const newErrors = {};
    
    if (!formData.name.trim()) newErrors.name = 'Name is required';
    if (!formData.email.trim()) newErrors.email = 'Email is required';
    if (!formData.message.trim()) newErrors.message = 'Message is required';
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  }, [formData]);
  
  // Memoized submit handler
  const handleSubmit = useCallback((event) => {
    event.preventDefault();
    if (validateForm()) {
      onSubmit(formData);
    }
  }, [formData, validateForm, onSubmit]);
  
  return (
    <form onSubmit={handleSubmit} className="optimized-form">
      <OptimizedInput
        label="Name"
        value={formData.name}
        onChange={handleFieldChange('name')}
        error={errors.name}
      />
      <OptimizedInput
        label="Email"
        type="email"
        value={formData.email}
        onChange={handleFieldChange('email')}
        error={errors.email}
      />
      <OptimizedTextarea
        label="Message"
        value={formData.message}
        onChange={handleFieldChange('message')}
        error={errors.message}
      />
      <button type="submit">Submit</button>
    </form>
  );
}

// Memoized input components
const OptimizedInput = memo(function OptimizedInput({ 
  label, 
  value, 
  onChange, 
  error, 
  type = 'text' 
}) {
  console.log(`🔄 Rendering input: ${label}`);
  
  return (
    <div className="form-group">
      <label>{label}</label>
      <input
        type={type}
        value={value}
        onChange={onChange}
        className={error ? 'error' : ''}
      />
      {error && <span className="error-text">{error}</span>}
    </div>
  );
});

const OptimizedTextarea = memo(function OptimizedTextarea({ 
  label, 
  value, 
  onChange, 
  error 
}) {
  console.log(`🔄 Rendering textarea: ${label}`);
  
  return (
    <div className="form-group">
      <label>{label}</label>
      <textarea
        value={value}
        onChange={onChange}
        className={error ? 'error' : ''}
        rows="4"
      />
      {error && <span className="error-text">{error}</span>}
    </div>
  );
});
```

**Example 2: Virtual Scrolling and Large Lists:**
```jsx
// Virtual scrolling implementation
function VirtualScrollList({ items, itemHeight = 50, containerHeight = 400 }) {
  const [scrollTop, setScrollTop] = useState(0);
  const containerRef = useRef();
  
  // Calculate visible range
  const visibleRange = useMemo(() => {
    const startIndex = Math.floor(scrollTop / itemHeight);
    const endIndex = Math.min(
      startIndex + Math.ceil(containerHeight / itemHeight) + 1,
      items.length
    );
    
    return { startIndex, endIndex };
  }, [scrollTop, itemHeight, containerHeight, items.length]);
  
  // Get visible items
  const visibleItems = useMemo(() => {
    return items.slice(visibleRange.startIndex, visibleRange.endIndex);
  }, [items, visibleRange]);
  
  // Handle scroll
  const handleScroll = useCallback((event) => {
    setScrollTop(event.target.scrollTop);
  }, []);
  
  // Total height for scrollbar
  const totalHeight = items.length * itemHeight;
  
  // Offset for visible items
  const offsetY = visibleRange.startIndex * itemHeight;
  
  return (
    <div
      ref={containerRef}
      className="virtual-scroll-container"
      style={{ height: containerHeight, overflowY: 'auto' }}
      onScroll={handleScroll}
    >
      <div style={{ height: totalHeight, position: 'relative' }}>
        <div
          style={{
            transform: `translateY(${offsetY}px)`,
            position: 'absolute',
            top: 0,
            left: 0,
            right: 0
          }}
        >
          {visibleItems.map((item, index) => (
            <VirtualListItem
              key={visibleRange.startIndex + index}
              item={item}
              height={itemHeight}
              index={visibleRange.startIndex + index}
            />
          ))}
        </div>
      </div>
    </div>
  );
}

const VirtualListItem = memo(function VirtualListItem({ item, height, index }) {
  return (
    <div
      className="virtual-list-item"
      style={{ height, display: 'flex', alignItems: 'center', padding: '0 16px' }}
    >
      <span className="item-index">#{index}</span>
      <span className="item-content">{item.name}</span>
      <span className="item-value">{item.value}</span>
    </div>
  );
});

// Usage example
function LargeListDemo() {
  const [itemCount, setItemCount] = useState(10000);
  
  const items = useMemo(() => {
    console.log(`🔄 Generating ${itemCount} items...`);
    return Array.from({ length: itemCount }, (_, index) => ({
      id: index,
      name: `Item ${index + 1}`,
      value: Math.floor(Math.random() * 1000)
    }));
  }, [itemCount]);
  
  return (
    <div className="large-list-demo">
      <div className="controls">
        <label>
          Item Count:
          <input
            type="number"
            value={itemCount}
            onChange={(e) => setItemCount(parseInt(e.target.value) || 0)}
            min="0"
            max="100000"
          />
        </label>
      </div>
      
      <div className="list-container">
        <h3>Virtual Scrolling ({items.length} items)</h3>
        <VirtualScrollList
          items={items}
          itemHeight={60}
          containerHeight={400}
        />
      </div>
    </div>
  );
}
```

**Example 3: Performance Monitoring and Profiling:**
```jsx
// Performance monitoring hook
function usePerformanceMonitor(componentName) {
  const renderCount = useRef(0);
  const lastRenderTime = useRef(Date.now());
  const [performanceData, setPerformanceData] = useState({
    renderCount: 0,
    averageRenderTime: 0,
    lastRenderDuration: 0
  });
  
  useEffect(() => {
    renderCount.current += 1;
    const now = Date.now();
    const renderDuration = now - lastRenderTime.current;
    
    setPerformanceData(prev => ({
      renderCount: renderCount.current,
      lastRenderDuration: renderDuration,
      averageRenderTime: prev.averageRenderTime === 0 
        ? renderDuration 
        : (prev.averageRenderTime + renderDuration) / 2
    }));
    
    lastRenderTime.current = now;
    
    // Log performance data
    console.log(`📊 ${componentName} Performance:`, {
      renders: renderCount.current,
      lastDuration: renderDuration,
      avgDuration: performanceData.averageRenderTime
    });
  });
  
  return performanceData;
}

// Component with performance monitoring
function MonitoredComponent({ data, onUpdate }) {
  const performanceData = usePerformanceMonitor('MonitoredComponent');
  
  const processedData = useMemo(() => {
    const start = performance.now();
    const result = data.map(item => ({ ...item, processed: true }));
    const duration = performance.now() - start;
    console.log(`⏱️ Data processing took ${duration.toFixed(2)}ms`);
    return result;
  }, [data]);
  
  return (
    <div className="monitored-component">
      <div className="performance-info">
        <h4>Performance Metrics</h4>
        <p>Renders: {performanceData.renderCount}</p>
        <p>Last Render: {performanceData.lastRenderDuration}ms</p>
        <p>Avg Render: {performanceData.averageRenderTime.toFixed(2)}ms</p>
      </div>
      
      <div className="component-content">
        <h3>Processed Data ({processedData.length} items)</h3>
        <button onClick={() => onUpdate(processedData)}>
          Update Data
        </button>
      </div>
    </div>
  );
}

// Memory usage monitoring
function useMemoryMonitor() {
  const [memoryInfo, setMemoryInfo] = useState(null);
  
  useEffect(() => {
    const updateMemoryInfo = () => {
      if ('memory' in performance) {
        setMemoryInfo({
          usedJSHeapSize: performance.memory.usedJSHeapSize,
          totalJSHeapSize: performance.memory.totalJSHeapSize,
          jsHeapSizeLimit: performance.memory.jsHeapSizeLimit
        });
      }
    };
    
    updateMemoryInfo();
    const interval = setInterval(updateMemoryInfo, 1000);
    
    return () => clearInterval(interval);
  }, []);
  
  return memoryInfo;
}

// Performance dashboard
function PerformanceDashboard() {
  const memoryInfo = useMemoryMonitor();
  const [componentData, setComponentData] = useState(
    Array.from({ length: 1000 }, (_, i) => ({ id: i, value: Math.random() }))
  );
  
  const handleUpdateData = useCallback(() => {
    setComponentData(prev => 
      prev.map(item => ({ ...item, value: Math.random() }))
    );
  }, []);
  
  const formatBytes = (bytes) => {
    return (bytes / 1024 / 1024).toFixed(2) + ' MB';
  };
  
  return (
    <div className="performance-dashboard">
      <h2>Performance Dashboard</h2>
      
      {memoryInfo && (
        <div className="memory-info">
          <h3>Memory Usage</h3>
          <p>Used: {formatBytes(memoryInfo.usedJSHeapSize)}</p>
          <p>Total: {formatBytes(memoryInfo.totalJSHeapSize)}</p>
          <p>Limit: {formatBytes(memoryInfo.jsHeapSizeLimit)}</p>
        </div>
      )}
      
      <MonitoredComponent 
        data={componentData} 
        onUpdate={handleUpdateData} 
      />
    </div>
  );
}
```

**Performance Best Practices:**
```jsx
// 1. Avoid inline objects and functions
// ❌ Bad
function BadComponent({ items }) {
  return (
    <div>
      {items.map(item => (
        <ItemComponent
          key={item.id}
          item={item}
          style={{ margin: '10px' }} // New object every render
          onClick={() => console.log(item.id)} // New function every render
        />
      ))}
    </div>
  );
}

// ✅ Good
const itemStyle = { margin: '10px' }; // Defined outside component

function GoodComponent({ items, onItemClick }) {
  const handleItemClick = useCallback((itemId) => {
    onItemClick(itemId);
  }, [onItemClick]);
  
  return (
    <div>
      {items.map(item => (
        <ItemComponent
          key={item.id}
          item={item}
          style={itemStyle}
          onClick={() => handleItemClick(item.id)}
        />
      ))}
    </div>
  );
}

// 2. Optimize context usage
const OptimizedContext = createContext();

function OptimizedProvider({ children }) {
  const [state, setState] = useState({ user: null, settings: {} });
  
  // Split context values to prevent unnecessary re-renders
  const userValue = useMemo(() => ({ 
    user: state.user, 
    setUser: (user) => setState(prev => ({ ...prev, user })) 
  }), [state.user]);
  
  const settingsValue = useMemo(() => ({ 
    settings: state.settings, 
    setSettings: (settings) => setState(prev => ({ ...prev, settings })) 
  }), [state.settings]);
  
  return (
    <UserContext.Provider value={userValue}>
      <SettingsContext.Provider value={settingsValue}>
        {children}
      </SettingsContext.Provider>
    </UserContext.Provider>
  );
}

// 3. Debounce expensive operations
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);
  
  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);
    
    return () => clearTimeout(handler);
  }, [value, delay]);
  
  return debouncedValue;
}

function SearchComponent({ onSearch }) {
  const [searchTerm, setSearchTerm] = useState('');
  const debouncedSearchTerm = useDebounce(searchTerm, 300);
  
  useEffect(() => {
    if (debouncedSearchTerm) {
      onSearch(debouncedSearchTerm);
    }
  }, [debouncedSearchTerm, onSearch]);
  
  return (
    <input
      type="text"
      value={searchTerm}
      onChange={(e) => setSearchTerm(e.target.value)}
      placeholder="Search..."
    />
  );
}
```

**Interview Questions:**
1. What are the main performance optimization techniques in React?
2. When should you use React.memo vs useMemo vs useCallback?
3. How do you identify performance bottlenecks in React apps?
4. What is virtual scrolling and when should you use it?
5. How do you optimize large lists in React?
6. What are the common causes of unnecessary re-renders?
7. How do you measure and monitor React app performance?
8. What is the difference between memoization and caching?
9. How do you optimize context usage for performance?
10. What tools can you use for React performance profiling?

---## 
🧩 WEEK 9–10: Testing and Advanced Patterns

### 🔹 Day 35–36: Testing React Applications - DEEP DIVE

**Definition (English):**
Testing React applications involves verifying that components behave correctly under different conditions. This includes unit testing individual components, integration testing component interactions, and end-to-end testing complete user workflows. Popular tools include Jest for test running, React Testing Library for component testing, and Cypress for E2E testing.

**Hinglish Deep Explanation:**
React testing ka matlab hai components aur application ka behavior verify karna. Isme unit tests (individual components), integration tests (components ke beech interaction), aur end-to-end tests (complete user flows) shamil hain. Main tools hain Jest (test runner), React Testing Library (component testing), aur Cypress (E2E testing).

**React Testing Deep Understanding:**

**1. Basic Component Testing with React Testing Library:**
```jsx
// Component to test
function Counter({ initialValue = 0, onCountChange }) {
  const [count, setCount] = useState(initialValue);
  
  const increment = () => {
    const newCount = count + 1;
    setCount(newCount);
    onCountChange?.(newCount);
  };
  
  const decrement = () => {
    const newCount = count - 1;
    setCount(newCount);
    onCountChange?.(newCount);
  };
  
  const reset = () => {
    setCount(initialValue);
    onCountChange?.(initialValue);
  };
  
  return (
    <div data-testid="counter">
      <h2>Counter: {count}</h2>
      <button onClick={increment} data-testid="increment-btn">
        Increment
      </button>
      <button onClick={decrement} data-testid="decrement-btn">
        Decrement
      </button>
      <button onClick={reset} data-testid="reset-btn">
        Reset
      </button>
    </div>
  );
}

// Test file: Counter.test.jsx
import { render, screen, fireEvent } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import Counter from './Counter';

describe('Counter Component', () => {
  test('renders with initial value', () => {
    render(<Counter initialValue={5} />);
    
    expect(screen.getByText('Counter: 5')).toBeInTheDocument();
  });
  
  test('increments count when increment button is clicked', async () => {
    const user = userEvent.setup();
    render(<Counter />);
    
    const incrementBtn = screen.getByTestId('increment-btn');
    await user.click(incrementBtn);
    
    expect(screen.getByText('Counter: 1')).toBeInTheDocument();
  });
  
  test('decrements count when decrement button is clicked', async () => {
    const user = userEvent.setup();
    render(<Counter initialValue={5} />);
    
    const decrementBtn = screen.getByTestId('decrement-btn');
    await user.click(decrementBtn);
    
    expect(screen.getByText('Counter: 4')).toBeInTheDocument();
  });
  
  test('resets count to initial value', async () => {
    const user = userEvent.setup();
    render(<Counter initialValue={10} />);
    
    // Change the count first
    await user.click(screen.getByTestId('increment-btn'));
    expect(screen.getByText('Counter: 11')).toBeInTheDocument();
    
    // Then reset
    await user.click(screen.getByTestId('reset-btn'));
    expect(screen.getByText('Counter: 10')).toBeInTheDocument();
  });
  
  test('calls onCountChange callback when count changes', async () => {
    const user = userEvent.setup();
    const mockOnCountChange = jest.fn();
    
    render(<Counter onCountChange={mockOnCountChange} />);
    
    await user.click(screen.getByTestId('increment-btn'));
    
    expect(mockOnCountChange).toHaveBeenCalledWith(1);
    expect(mockOnCountChange).toHaveBeenCalledTimes(1);
  });
  
  test('handles multiple rapid clicks correctly', async () => {
    const user = userEvent.setup();
    render(<Counter />);
    
    const incrementBtn = screen.getByTestId('increment-btn');
    
    // Click multiple times rapidly
    await user.click(incrementBtn);
    await user.click(incrementBtn);
    await user.click(incrementBtn);
    
    expect(screen.getByText('Counter: 3')).toBeInTheDocument();
  });
});
```

**Example 1: Testing Forms and User Interactions:**
```jsx
// UserForm component
function UserForm({ onSubmit, initialData = {} }) {
  const [formData, setFormData] = useState({
    name: initialData.name || '',
    email: initialData.email || '',
    age: initialData.age || '',
    interests: initialData.interests || []
  });
  
  const [errors, setErrors] = useState({});
  const [isSubmitting, setIsSubmitting] = useState(false);
  
  const validateForm = () => {
    const newErrors = {};
    
    if (!formData.name.trim()) {
      newErrors.name = 'Name is required';
    }
    
    if (!formData.email.trim()) {
      newErrors.email = 'Email is required';
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = 'Email is invalid';
    }
    
    if (!formData.age || formData.age < 1) {
      newErrors.age = 'Age must be a positive number';
    }
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };
  
  const handleSubmit = async (e) => {
    e.preventDefault();
    
    if (!validateForm()) return;
    
    setIsSubmitting(true);
    
    try {
      await onSubmit(formData);
    } catch (error) {
      setErrors({ submit: error.message });
    } finally {
      setIsSubmitting(false);
    }
  };
  
  const handleInputChange = (field) => (e) => {
    const value = e.target.value;
    setFormData(prev => ({ ...prev, [field]: value }));
    
    // Clear error when user starts typing
    if (errors[field]) {
      setErrors(prev => ({ ...prev, [field]: '' }));
    }
  };
  
  const handleInterestChange = (interest) => {
    setFormData(prev => ({
      ...prev,
      interests: prev.interests.includes(interest)
        ? prev.interests.filter(i => i !== interest)
        : [...prev.interests, interest]
    }));
  };
  
  return (
    <form onSubmit={handleSubmit} data-testid="user-form">
      <div className="form-group">
        <label htmlFor="name">Name</label>
        <input
          id="name"
          type="text"
          value={formData.name}
          onChange={handleInputChange('name')}
          aria-invalid={!!errors.name}
          aria-describedby={errors.name ? 'name-error' : undefined}
        />
        {errors.name && (
          <div id="name-error" role="alert" className="error">
            {errors.name}
          </div>
        )}
      </div>
      
      <div className="form-group">
        <label htmlFor="email">Email</label>
        <input
          id="email"
          type="email"
          value={formData.email}
          onChange={handleInputChange('email')}
          aria-invalid={!!errors.email}
          aria-describedby={errors.email ? 'email-error' : undefined}
        />
        {errors.email && (
          <div id="email-error" role="alert" className="error">
            {errors.email}
          </div>
        )}
      </div>
      
      <div className="form-group">
        <label htmlFor="age">Age</label>
        <input
          id="age"
          type="number"
          value={formData.age}
          onChange={handleInputChange('age')}
          aria-invalid={!!errors.age}
          aria-describedby={errors.age ? 'age-error' : undefined}
        />
        {errors.age && (
          <div id="age-error" role="alert" className="error">
            {errors.age}
          </div>
        )}
      </div>
      
      <fieldset>
        <legend>Interests</legend>
        {['Technology', 'Sports', 'Music', 'Travel'].map(interest => (
          <label key={interest}>
            <input
              type="checkbox"
              checked={formData.interests.includes(interest)}
              onChange={() => handleInterestChange(interest)}
            />
            {interest}
          </label>
        ))}
      </fieldset>
      
      {errors.submit && (
        <div role="alert" className="error">
          {errors.submit}
        </div>
      )}
      
      <button type="submit" disabled={isSubmitting}>
        {isSubmitting ? 'Submitting...' : 'Submit'}
      </button>
    </form>
  );
}

// UserForm.test.jsx
import { render, screen, waitFor } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import UserForm from './UserForm';

describe('UserForm', () => {
  const mockOnSubmit = jest.fn();
  
  beforeEach(() => {
    mockOnSubmit.mockClear();
  });
  
  test('renders form fields correctly', () => {
    render(<UserForm onSubmit={mockOnSubmit} />);
    
    expect(screen.getByLabelText(/name/i)).toBeInTheDocument();
    expect(screen.getByLabelText(/email/i)).toBeInTheDocument();
    expect(screen.getByLabelText(/age/i)).toBeInTheDocument();
    expect(screen.getByRole('group', { name: /interests/i })).toBeInTheDocument();
    expect(screen.getByRole('button', { name: /submit/i })).toBeInTheDocument();
  });
  
  test('populates form with initial data', () => {
    const initialData = {
      name: 'John Doe',
      email: 'john@example.com',
      age: '25',
      interests: ['Technology', 'Sports']
    };
    
    render(<UserForm onSubmit={mockOnSubmit} initialData={initialData} />);
    
    expect(screen.getByDisplayValue('John Doe')).toBeInTheDocument();
    expect(screen.getByDisplayValue('john@example.com')).toBeInTheDocument();
    expect(screen.getByDisplayValue('25')).toBeInTheDocument();
    expect(screen.getByRole('checkbox', { name: /technology/i })).toBeChecked();
    expect(screen.getByRole('checkbox', { name: /sports/i })).toBeChecked();
  });
  
  test('shows validation errors for empty required fields', async () => {
    const user = userEvent.setup();
    render(<UserForm onSubmit={mockOnSubmit} />);
    
    const submitButton = screen.getByRole('button', { name: /submit/i });
    await user.click(submitButton);
    
    expect(screen.getByText('Name is required')).toBeInTheDocument();
    expect(screen.getByText('Email is required')).toBeInTheDocument();
    expect(screen.getByText('Age must be a positive number')).toBeInTheDocument();
    expect(mockOnSubmit).not.toHaveBeenCalled();
  });
  
  test('shows email validation error for invalid email', async () => {
    const user = userEvent.setup();
    render(<UserForm onSubmit={mockOnSubmit} />);
    
    await user.type(screen.getByLabelText(/email/i), 'invalid-email');
    await user.click(screen.getByRole('button', { name: /submit/i }));
    
    expect(screen.getByText('Email is invalid')).toBeInTheDocument();
  });
  
  test('clears validation errors when user starts typing', async () => {
    const user = userEvent.setup();
    render(<UserForm onSubmit={mockOnSubmit} />);
    
    // Trigger validation error
    await user.click(screen.getByRole('button', { name: /submit/i }));
    expect(screen.getByText('Name is required')).toBeInTheDocument();
    
    // Start typing to clear error
    await user.type(screen.getByLabelText(/name/i), 'J');
    expect(screen.queryByText('Name is required')).not.toBeInTheDocument();
  });
  
  test('handles interest selection correctly', async () => {
    const user = userEvent.setup();
    render(<UserForm onSubmit={mockOnSubmit} />);
    
    const technologyCheckbox = screen.getByRole('checkbox', { name: /technology/i });
    const sportsCheckbox = screen.getByRole('checkbox', { name: /sports/i });
    
    // Select interests
    await user.click(technologyCheckbox);
    await user.click(sportsCheckbox);
    
    expect(technologyCheckbox).toBeChecked();
    expect(sportsCheckbox).toBeChecked();
    
    // Deselect one interest
    await user.click(technologyCheckbox);
    expect(technologyCheckbox).not.toBeChecked();
    expect(sportsCheckbox).toBeChecked();
  });
  
  test('submits form with valid data', async () => {
    const user = userEvent.setup();
    mockOnSubmit.mockResolvedValue();
    
    render(<UserForm onSubmit={mockOnSubmit} />);
    
    // Fill out form
    await user.type(screen.getByLabelText(/name/i), 'John Doe');
    await user.type(screen.getByLabelText(/email/i), 'john@example.com');
    await user.type(screen.getByLabelText(/age/i), '25');
    await user.click(screen.getByRole('checkbox', { name: /technology/i }));
    
    // Submit form
    await user.click(screen.getByRole('button', { name: /submit/i }));
    
    await waitFor(() => {
      expect(mockOnSubmit).toHaveBeenCalledWith({
        name: 'John Doe',
        email: 'john@example.com',
        age: '25',
        interests: ['Technology']
      });
    });
  });
  
  test('handles submission error', async () => {
    const user = userEvent.setup();
    const errorMessage = 'Submission failed';
    mockOnSubmit.mockRejectedValue(new Error(errorMessage));
    
    render(<UserForm onSubmit={mockOnSubmit} />);
    
    // Fill out form with valid data
    await user.type(screen.getByLabelText(/name/i), 'John Doe');
    await user.type(screen.getByLabelText(/email/i), 'john@example.com');
    await user.type(screen.getByLabelText(/age/i), '25');
    
    // Submit form
    await user.click(screen.getByRole('button', { name: /submit/i }));
    
    await waitFor(() => {
      expect(screen.getByText(errorMessage)).toBeInTheDocument();
    });
  });
  
  test('disables submit button during submission', async () => {
    const user = userEvent.setup();
    let resolveSubmit;
    mockOnSubmit.mockImplementation(() => new Promise(resolve => {
      resolveSubmit = resolve;
    }));
    
    render(<UserForm onSubmit={mockOnSubmit} />);
    
    // Fill out form
    await user.type(screen.getByLabelText(/name/i), 'John Doe');
    await user.type(screen.getByLabelText(/email/i), 'john@example.com');
    await user.type(screen.getByLabelText(/age/i), '25');
    
    // Submit form
    const submitButton = screen.getByRole('button', { name: /submit/i });
    await user.click(submitButton);
    
    // Button should be disabled and show loading text
    expect(screen.getByRole('button', { name: /submitting/i })).toBeDisabled();
    
    // Resolve the promise
    resolveSubmit();
    
    await waitFor(() => {
      expect(screen.getByRole('button', { name: /submit/i })).not.toBeDisabled();
    });
  });
});
```

**Example 2: Testing Hooks and Context:**
```jsx
// Custom hook to test
function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);
  
  const increment = useCallback(() => {
    setCount(prev => prev + 1);
  }, []);
  
  const decrement = useCallback(() => {
    setCount(prev => prev - 1);
  }, []);
  
  const reset = useCallback(() => {
    setCount(initialValue);
  }, [initialValue]);
  
  return { count, increment, decrement, reset };
}

// Hook test
import { renderHook, act } from '@testing-library/react';
import useCounter from './useCounter';

describe('useCounter', () => {
  test('initializes with default value', () => {
    const { result } = renderHook(() => useCounter());
    
    expect(result.current.count).toBe(0);
  });
  
  test('initializes with custom value', () => {
    const { result } = renderHook(() => useCounter(10));
    
    expect(result.current.count).toBe(10);
  });
  
  test('increments count', () => {
    const { result } = renderHook(() => useCounter());
    
    act(() => {
      result.current.increment();
    });
    
    expect(result.current.count).toBe(1);
  });
  
  test('decrements count', () => {
    const { result } = renderHook(() => useCounter(5));
    
    act(() => {
      result.current.decrement();
    });
    
    expect(result.current.count).toBe(4);
  });
  
  test('resets to initial value', () => {
    const { result } = renderHook(() => useCounter(10));
    
    act(() => {
      result.current.increment();
      result.current.increment();
    });
    
    expect(result.current.count).toBe(12);
    
    act(() => {
      result.current.reset();
    });
    
    expect(result.current.count).toBe(10);
  });
});

// Context testing
const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');
  
  const toggleTheme = () => {
    setTheme(prev => prev === 'light' ? 'dark' : 'light');
  };
  
  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

function useTheme() {
  const context = useContext(ThemeContext);
  if (!context) {
    throw new Error('useTheme must be used within ThemeProvider');
  }
  return context;
}

// Component using context
function ThemedButton() {
  const { theme, toggleTheme } = useTheme();
  
  return (
    <button 
      onClick={toggleTheme}
      className={`button-${theme}`}
      data-testid="themed-button"
    >
      Current theme: {theme}
    </button>
  );
}

// Context tests
describe('ThemeContext', () => {
  test('provides theme context to children', () => {
    render(
      <ThemeProvider>
        <ThemedButton />
      </ThemeProvider>
    );
    
    expect(screen.getByText('Current theme: light')).toBeInTheDocument();
  });
  
  test('toggles theme when button is clicked', async () => {
    const user = userEvent.setup();
    
    render(
      <ThemeProvider>
        <ThemedButton />
      </ThemeProvider>
    );
    
    const button = screen.getByTestId('themed-button');
    
    await user.click(button);
    expect(screen.getByText('Current theme: dark')).toBeInTheDocument();
    
    await user.click(button);
    expect(screen.getByText('Current theme: light')).toBeInTheDocument();
  });
  
  test('throws error when useTheme is used outside provider', () => {
    // Suppress console.error for this test
    const consoleSpy = jest.spyOn(console, 'error').mockImplementation(() => {});
    
    expect(() => {
      render(<ThemedButton />);
    }).toThrow('useTheme must be used within ThemeProvider');
    
    consoleSpy.mockRestore();
  });
});
```

**Example 3: Testing Async Operations and API Calls:**
```jsx
// Component with API calls
function UserList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    fetchUsers();
  }, []);
  
  const fetchUsers = async () => {
    try {
      setLoading(true);
      setError(null);
      
      const response = await fetch('/api/users');
      if (!response.ok) {
        throw new Error('Failed to fetch users');
      }
      
      const userData = await response.json();
      setUsers(userData);
    } catch (err) {
      setError(err.message);
    } finally {
      setLoading(false);
    }
  };
  
  const deleteUser = async (userId) => {
    try {
      const response = await fetch(`/api/users/${userId}`, {
        method: 'DELETE'
      });
      
      if (!response.ok) {
        throw new Error('Failed to delete user');
      }
      
      setUsers(prev => prev.filter(user => user.id !== userId));
    } catch (err) {
      setError(err.message);
    }
  };
  
  if (loading) return <div data-testid="loading">Loading...</div>;
  if (error) return <div data-testid="error">Error: {error}</div>;
  
  return (
    <div data-testid="user-list">
      <h2>Users</h2>
      {users.length === 0 ? (
        <p data-testid="no-users">No users found</p>
      ) : (
        <ul>
          {users.map(user => (
            <li key={user.id} data-testid={`user-${user.id}`}>
              <span>{user.name} ({user.email})</span>
              <button 
                onClick={() => deleteUser(user.id)}
                data-testid={`delete-${user.id}`}
              >
                Delete
              </button>
            </li>
          ))}
        </ul>
      )}
      <button onClick={fetchUsers} data-testid="refresh-btn">
        Refresh
      </button>
    </div>
  );
}

// API tests with mocking
import { render, screen, waitFor } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import UserList from './UserList';

// Mock fetch globally
global.fetch = jest.fn();

describe('UserList', () => {
  beforeEach(() => {
    fetch.mockClear();
  });
  
  test('shows loading state initially', () => {
    fetch.mockImplementation(() => new Promise(() => {})); // Never resolves
    
    render(<UserList />);
    
    expect(screen.getByTestId('loading')).toBeInTheDocument();
  });
  
  test('displays users after successful fetch', async () => {
    const mockUsers = [
      { id: 1, name: 'John Doe', email: 'john@example.com' },
      { id: 2, name: 'Jane Smith', email: 'jane@example.com' }
    ];
    
    fetch.mockResolvedValueOnce({
      ok: true,
      json: async () => mockUsers
    });
    
    render(<UserList />);
    
    await waitFor(() => {
      expect(screen.getByTestId('user-list')).toBeInTheDocument();
    });
    
    expect(screen.getByText('John Doe (john@example.com)')).toBeInTheDocument();
    expect(screen.getByText('Jane Smith (jane@example.com)')).toBeInTheDocument();
  });
  
  test('displays error message when fetch fails', async () => {
    fetch.mockRejectedValueOnce(new Error('Network error'));
    
    render(<UserList />);
    
    await waitFor(() => {
      expect(screen.getByTestId('error')).toBeInTheDocument();
    });
    
    expect(screen.getByText('Error: Network error')).toBeInTheDocument();
  });
  
  test('displays error when API returns error status', async () => {
    fetch.mockResolvedValueOnce({
      ok: false,
      status: 500
    });
    
    render(<UserList />);
    
    await waitFor(() => {
      expect(screen.getByTestId('error')).toBeInTheDocument();
    });
    
    expect(screen.getByText('Error: Failed to fetch users')).toBeInTheDocument();
  });
  
  test('shows no users message when list is empty', async () => {
    fetch.mockResolvedValueOnce({
      ok: true,
      json: async () => []
    });
    
    render(<UserList />);
    
    await waitFor(() => {
      expect(screen.getByTestId('no-users')).toBeInTheDocument();
    });
  });
  
  test('deletes user when delete button is clicked', async () => {
    const user = userEvent.setup();
    const mockUsers = [
      { id: 1, name: 'John Doe', email: 'john@example.com' },
      { id: 2, name: 'Jane Smith', email: 'jane@example.com' }
    ];
    
    // Mock initial fetch
    fetch.mockResolvedValueOnce({
      ok: true,
      json: async () => mockUsers
    });
    
    render(<UserList />);
    
    await waitFor(() => {
      expect(screen.getByTestId('user-1')).toBeInTheDocument();
    });
    
    // Mock delete request
    fetch.mockResolvedValueOnce({ ok: true });
    
    await user.click(screen.getByTestId('delete-1'));
    
    await waitFor(() => {
      expect(screen.queryByTestId('user-1')).not.toBeInTheDocument();
    });
    
    expect(screen.getByTestId('user-2')).toBeInTheDocument();
    expect(fetch).toHaveBeenCalledWith('/api/users/1', { method: 'DELETE' });
  });
  
  test('refreshes user list when refresh button is clicked', async () => {
    const user = userEvent.setup();
    const initialUsers = [{ id: 1, name: 'John', email: 'john@example.com' }];
    const refreshedUsers = [
      { id: 1, name: 'John', email: 'john@example.com' },
      { id: 2, name: 'Jane', email: 'jane@example.com' }
    ];
    
    // Mock initial fetch
    fetch.mockResolvedValueOnce({
      ok: true,
      json: async () => initialUsers
    });
    
    render(<UserList />);
    
    await waitFor(() => {
      expect(screen.getByTestId('user-1')).toBeInTheDocument();
    });
    
    // Mock refresh fetch
    fetch.mockResolvedValueOnce({
      ok: true,
      json: async () => refreshedUsers
    });
    
    await user.click(screen.getByTestId('refresh-btn'));
    
    await waitFor(() => {
      expect(screen.getByTestId('user-2')).toBeInTheDocument();
    });
    
    expect(fetch).toHaveBeenCalledTimes(2);
  });
});
```

**Testing Best Practices:**
```jsx
// 1. Custom render function with providers
function renderWithProviders(ui, options = {}) {
  const {
    initialState = {},
    store = createStore(rootReducer, initialState),
    ...renderOptions
  } = options;
  
  function Wrapper({ children }) {
    return (
      <Provider store={store}>
        <ThemeProvider>
          <Router>
            {children}
          </Router>
        </ThemeProvider>
      </Provider>
    );
  }
  
  return render(ui, { wrapper: Wrapper, ...renderOptions });
}

// 2. Test utilities
const testUtils = {
  // Fill form helper
  fillForm: async (user, formData) => {
    for (const [field, value] of Object.entries(formData)) {
      const input = screen.getByLabelText(new RegExp(field, 'i'));
      await user.clear(input);
      await user.type(input, value);
    }
  },
  
  // Wait for loading to finish
  waitForLoadingToFinish: () => {
    return waitFor(() => {
      expect(screen.queryByTestId('loading')).not.toBeInTheDocument();
    });
  },
  
  // Mock API responses
  mockApiSuccess: (data) => {
    fetch.mockResolvedValueOnce({
      ok: true,
      json: async () => data
    });
  },
  
  mockApiError: (error) => {
    fetch.mockRejectedValueOnce(new Error(error));
  }
};

// 3. Setup and teardown
beforeEach(() => {
  // Clear all mocks
  jest.clearAllMocks();
  
  // Reset fetch mock
  fetch.mockClear();
  
  // Clear local storage
  localStorage.clear();
});

afterEach(() => {
  // Clean up any timers
  jest.runOnlyPendingTimers();
  jest.useRealTimers();
});
```

**Interview Questions:**
1. What are the different types of testing in React applications?
2. What is React Testing Library and how is it different from Enzyme?
3. How do you test components that use hooks?
4. How do you test components that use context?
5. How do you mock API calls in tests?
6. What are the best practices for writing React tests?
7. How do you test user interactions and events?
8. How do you test async operations and loading states?
9. What is the difference between unit, integration, and E2E tests?
10. How do you test custom hooks?

---### 🔹 
Day 37–38: Advanced Hooks - DEEP DIVE

**Definition (English):**
Advanced React hooks include useReducer for complex state management, useRef for DOM access and mutable values, useMemo and useCallback for performance optimization, and custom hooks for reusable logic. These hooks provide powerful patterns for managing state, side effects, and component behavior in functional components.

**Hinglish Deep Explanation:**
Advanced hooks React ke powerful features hain jo complex scenarios handle karte hain. useReducer complex state management ke liye, useRef DOM elements aur mutable values ke liye, useMemo/useCallback performance ke liye, aur custom hooks reusable logic ke liye use hote hain. Ye functional components ko class components se bhi zyada powerful banate hain.

**Advanced Hooks Deep Understanding:**

**1. useReducer for Complex State Management:**
```jsx
// Shopping cart reducer
const cartReducer = (state, action) => {
  switch (action.type) {
    case 'ADD_ITEM':
      const existingItem = state.items.find(item => item.id === action.payload.id);
      if (existingItem) {
        return {
          ...state,
          items: state.items.map(item =>
            item.id === action.payload.id
              ? { ...item, quantity: item.quantity + 1 }
              : item
          )
        };
      }
      return {
        ...state,
        items: [...state.items, { ...action.payload, quantity: 1 }]
      };
    
    case 'REMOVE_ITEM':
      return {
        ...state,
        items: state.items.filter(item => item.id !== action.payload)
      };
    
    case 'UPDATE_QUANTITY':
      return {
        ...state,
        items: state.items.map(item =>
          item.id === action.payload.id
            ? { ...item, quantity: Math.max(0, action.payload.quantity) }
            : item
        ).filter(item => item.quantity > 0)
      };
    
    case 'CLEAR_CART':
      return { ...state, items: [] };
    
    case 'APPLY_DISCOUNT':
      return { ...state, discount: action.payload };
    
    case 'SET_SHIPPING':
      return { ...state, shipping: action.payload };
    
    default:
      return state;
  }
};

// Initial state
const initialCartState = {
  items: [],
  discount: null,
  shipping: { method: 'standard', cost: 0 }
};

// Shopping cart component using useReducer
function ShoppingCart() {
  const [cartState, dispatch] = useReducer(cartReducer, initialCartState);
  
  // Computed values
  const subtotal = cartState.items.reduce(
    (sum, item) => sum + (item.price * item.quantity), 0
  );
  
  const discountAmount = cartState.discount 
    ? (subtotal * cartState.discount.percentage) / 100 
    : 0;
  
  const total = subtotal - discountAmount + cartState.shipping.cost;
  
  // Action creators
  const addItem = (product) => {
    dispatch({ type: 'ADD_ITEM', payload: product });
  };
  
  const removeItem = (productId) => {
    dispatch({ type: 'REMOVE_ITEM', payload: productId });
  };
  
  const updateQuantity = (productId, quantity) => {
    dispatch({ type: 'UPDATE_QUANTITY', payload: { id: productId, quantity } });
  };
  
  const clearCart = () => {
    dispatch({ type: 'CLEAR_CART' });
  };
  
  const applyDiscount = (discount) => {
    dispatch({ type: 'APPLY_DISCOUNT', payload: discount });
  };
  
  return (
    <div className="shopping-cart">
      <h2>Shopping Cart ({cartState.items.length} items)</h2>
      
      {cartState.items.length === 0 ? (
        <p>Your cart is empty</p>
      ) : (
        <>
          <div className="cart-items">
            {cartState.items.map(item => (
              <div key={item.id} className="cart-item">
                <span>{item.name}</span>
                <div className="quantity-controls">
                  <button onClick={() => updateQuantity(item.id, item.quantity - 1)}>
                    -
                  </button>
                  <span>{item.quantity}</span>
                  <button onClick={() => updateQuantity(item.id, item.quantity + 1)}>
                    +
                  </button>
                </div>
                <span>₹{(item.price * item.quantity).toLocaleString()}</span>
                <button onClick={() => removeItem(item.id)}>Remove</button>
              </div>
            ))}
          </div>
          
          <div className="cart-summary">
            <div>Subtotal: ₹{subtotal.toLocaleString()}</div>
            {cartState.discount && (
              <div>Discount: -₹{discountAmount.toLocaleString()}</div>
            )}
            <div>Shipping: ₹{cartState.shipping.cost.toLocaleString()}</div>
            <div className="total">Total: ₹{total.toLocaleString()}</div>
          </div>
          
          <button onClick={clearCart} className="clear-cart-btn">
            Clear Cart
          </button>
        </>
      )}
      
      {/* Sample products to add */}
      <div className="sample-products">
        <h3>Add Products</h3>
        {[
          { id: 1, name: 'Laptop', price: 50000 },
          { id: 2, name: 'Phone', price: 25000 },
          { id: 3, name: 'Headphones', price: 5000 }
        ].map(product => (
          <button key={product.id} onClick={() => addItem(product)}>
            Add {product.name} (₹{product.price.toLocaleString()})
          </button>
        ))}
      </div>
    </div>
  );
}
```

**Example 1: useRef for DOM Manipulation and Mutable Values:**
```jsx
// Advanced useRef patterns
function AdvancedRefExamples() {
  // 1. DOM element references
  const inputRef = useRef(null);
  const videoRef = useRef(null);
  const canvasRef = useRef(null);
  
  // 2. Mutable values that don't trigger re-renders
  const renderCount = useRef(0);
  const previousValue = useRef();
  const intervalId = useRef(null);
  
  // 3. Storing callback refs
  const callbackRef = useRef();
  
  const [count, setCount] = useState(0);
  const [isPlaying, setIsPlaying] = useState(false);
  
  // Track render count
  renderCount.current += 1;
  
  // Store previous value
  useEffect(() => {
    previousValue.current = count;
  });
  
  // Focus input
  const focusInput = () => {
    inputRef.current?.focus();
  };
  
  // Video controls
  const toggleVideo = () => {
    if (videoRef.current) {
      if (isPlaying) {
        videoRef.current.pause();
      } else {
        videoRef.current.play();
      }
      setIsPlaying(!isPlaying);
    }
  };
  
  // Canvas drawing
  const drawOnCanvas = () => {
    const canvas = canvasRef.current;
    if (canvas) {
      const ctx = canvas.getContext('2d');
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = '#007bff';
      ctx.fillRect(10, 10, 100, 100);
      ctx.fillStyle = 'white';
      ctx.font = '16px Arial';
      ctx.fillText(count.toString(), 50, 65);
    }
  };
  
  // Auto increment with cleanup
  const startAutoIncrement = () => {
    if (intervalId.current) return;
    
    intervalId.current = setInterval(() => {
      setCount(prev => prev + 1);
    }, 1000);
  };
  
  const stopAutoIncrement = () => {
    if (intervalId.current) {
      clearInterval(intervalId.current);
      intervalId.current = null;
    }
  };
  
  // Cleanup on unmount
  useEffect(() => {
    return () => {
      if (intervalId.current) {
        clearInterval(intervalId.current);
      }
    };
  }, []);
  
  // Callback ref example
  const measureElement = useCallback((node) => {
    if (node) {
      callbackRef.current = {
        width: node.offsetWidth,
        height: node.offsetHeight
      };
      console.log('Element dimensions:', callbackRef.current);
    }
  }, []);
  
  return (
    <div className="advanced-ref-examples">
      <h2>Advanced useRef Examples</h2>
      
      {/* Render tracking */}
      <div className="render-info">
        <p>Render count: {renderCount.current}</p>
        <p>Current count: {count}</p>
        <p>Previous count: {previousValue.current}</p>
      </div>
      
      {/* Input focus */}
      <div className="input-section">
        <input ref={inputRef} placeholder="Click button to focus" />
        <button onClick={focusInput}>Focus Input</button>
      </div>
      
      {/* Video controls */}
      <div className="video-section">
        <video
          ref={videoRef}
          width="300"
          height="200"
          src="/sample-video.mp4"
          onPlay={() => setIsPlaying(true)}
          onPause={() => setIsPlaying(false)}
        />
        <button onClick={toggleVideo}>
          {isPlaying ? 'Pause' : 'Play'}
        </button>
      </div>
      
      {/* Canvas drawing */}
      <div className="canvas-section">
        <canvas ref={canvasRef} width="200" height="150" />
        <button onClick={drawOnCanvas}>Draw on Canvas</button>
      </div>
      
      {/* Counter controls */}
      <div className="counter-section">
        <button onClick={() => setCount(count + 1)}>Increment</button>
        <button onClick={startAutoIncrement}>Start Auto</button>
        <button onClick={stopAutoIncrement}>Stop Auto</button>
      </div>
      
      {/* Callback ref */}
      <div ref={measureElement} className="measured-element">
        This element's dimensions are measured
      </div>
    </div>
  );
}
```

**Example 2: Custom Hooks for Reusable Logic:**
```jsx
// 1. useLocalStorage hook
function useLocalStorage(key, initialValue) {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error('Error reading from localStorage:', error);
      return initialValue;
    }
  });
  
  const setValue = (value) => {
    try {
      const valueToStore = value instanceof Function ? value(storedValue) : value;
      setStoredValue(valueToStore);
      window.localStorage.setItem(key, JSON.stringify(valueToStore));
    } catch (error) {
      console.error('Error writing to localStorage:', error);
    }
  };
  
  return [storedValue, setValue];
}

// 2. useDebounce hook
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);
  
  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);
    
    return () => {
      clearTimeout(handler);
    };
  }, [value, delay]);
  
  return debouncedValue;
}

// 3. useAsync hook
function useAsync(asyncFunction, dependencies = []) {
  const [state, setState] = useState({
    data: null,
    loading: true,
    error: null
  });
  
  useEffect(() => {
    let cancelled = false;
    
    setState({ data: null, loading: true, error: null });
    
    asyncFunction()
      .then(data => {
        if (!cancelled) {
          setState({ data, loading: false, error: null });
        }
      })
      .catch(error => {
        if (!cancelled) {
          setState({ data: null, loading: false, error });
        }
      });
    
    return () => {
      cancelled = true;
    };
  }, dependencies);
  
  return state;
}

// 4. useToggle hook
function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);
  
  const toggle = useCallback(() => setValue(prev => !prev), []);
  const setTrue = useCallback(() => setValue(true), []);
  const setFalse = useCallback(() => setValue(false), []);
  
  return [value, { toggle, setTrue, setFalse }];
}

// 5. useInterval hook
function useInterval(callback, delay) {
  const savedCallback = useRef();
  
  useEffect(() => {
    savedCallback.current = callback;
  }, [callback]);
  
  useEffect(() => {
    function tick() {
      savedCallback.current();
    }
    
    if (delay !== null) {
      const id = setInterval(tick, delay);
      return () => clearInterval(id);
    }
  }, [delay]);
}

// 6. useWindowSize hook
function useWindowSize() {
  const [windowSize, setWindowSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight
  });
  
  useEffect(() => {
    const handleResize = () => {
      setWindowSize({
        width: window.innerWidth,
        height: window.innerHeight
      });
    };
    
    window.addEventListener('resize', handleResize);
    return () => window.removeEventListener('resize', handleResize);
  }, []);
  
  return windowSize;
}

// 7. useOnClickOutside hook
function useOnClickOutside(ref, handler) {
  useEffect(() => {
    const listener = (event) => {
      if (!ref.current || ref.current.contains(event.target)) {
        return;
      }
      handler(event);
    };
    
    document.addEventListener('mousedown', listener);
    document.addEventListener('touchstart', listener);
    
    return () => {
      document.removeEventListener('mousedown', listener);
      document.removeEventListener('touchstart', listener);
    };
  }, [ref, handler]);
}

// Component using custom hooks
function CustomHooksDemo() {
  // Using custom hooks
  const [name, setName] = useLocalStorage('userName', '');
  const [searchTerm, setSearchTerm] = useState('');
  const debouncedSearchTerm = useDebounce(searchTerm, 500);
  const [isModalOpen, modalActions] = useToggle(false);
  const [count, setCount] = useState(0);
  const windowSize = useWindowSize();
  const modalRef = useRef();
  
  // Close modal on outside click
  useOnClickOutside(modalRef, modalActions.setFalse);
  
  // Auto increment counter
  useInterval(() => {
    setCount(prev => prev + 1);
  }, 1000);
  
  // Async data fetching
  const { data: searchResults, loading, error } = useAsync(async () => {
    if (!debouncedSearchTerm) return [];
    
    const response = await fetch(`/api/search?q=${debouncedSearchTerm}`);
    return response.json();
  }, [debouncedSearchTerm]);
  
  return (
    <div className="custom-hooks-demo">
      <h2>Custom Hooks Demo</h2>
      
      {/* Local storage */}
      <div className="section">
        <h3>Local Storage</h3>
        <input
          value={name}
          onChange={(e) => setName(e.target.value)}
          placeholder="Your name (saved to localStorage)"
        />
        <p>Stored name: {name}</p>
      </div>
      
      {/* Debounced search */}
      <div className="section">
        <h3>Debounced Search</h3>
        <input
          value={searchTerm}
          onChange={(e) => setSearchTerm(e.target.value)}
          placeholder="Search (debounced)"
        />
        <p>Debounced term: {debouncedSearchTerm}</p>
        {loading && <p>Searching...</p>}
        {error && <p>Error: {error.message}</p>}
        {searchResults && (
          <p>Found {searchResults.length} results</p>
        )}
      </div>
      
      {/* Toggle modal */}
      <div className="section">
        <h3>Toggle Modal</h3>
        <button onClick={modalActions.toggle}>
          {isModalOpen ? 'Close' : 'Open'} Modal
        </button>
        
        {isModalOpen && (
          <div className="modal-overlay">
            <div ref={modalRef} className="modal">
              <h4>Modal Content</h4>
              <p>Click outside to close</p>
              <button onClick={modalActions.setFalse}>Close</button>
            </div>
          </div>
        )}
      </div>
      
      {/* Auto counter */}
      <div className="section">
        <h3>Auto Counter</h3>
        <p>Count: {count}</p>
      </div>
      
      {/* Window size */}
      <div className="section">
        <h3>Window Size</h3>
        <p>Width: {windowSize.width}px</p>
        <p>Height: {windowSize.height}px</p>
        <p>Device: {windowSize.width < 768 ? 'Mobile' : 'Desktop'}</p>
      </div>
    </div>
  );
}
```

**Example 3: Advanced Hook Patterns:**
```jsx
// 1. useReducer with middleware
function useReducerWithMiddleware(reducer, initialState, middleware = []) {
  const [state, dispatch] = useReducer(reducer, initialState);
  
  const enhancedDispatch = useCallback((action) => {
    // Apply middleware
    const middlewareAPI = { getState: () => state, dispatch };
    const chain = middleware.map(mw => mw(middlewareAPI));
    const composedDispatch = chain.reduce((acc, mw) => mw(acc), dispatch);
    
    return composedDispatch(action);
  }, [state, middleware]);
  
  return [state, enhancedDispatch];
}

// Logger middleware
const loggerMiddleware = (store) => (next) => (action) => {
  console.log('Dispatching:', action);
  console.log('Previous state:', store.getState());
  const result = next(action);
  console.log('Next state:', store.getState());
  return result;
};

// 2. useStateWithHistory
function useStateWithHistory(initialValue, maxHistory = 10) {
  const [history, setHistory] = useState([initialValue]);
  const [currentIndex, setCurrentIndex] = useState(0);
  
  const currentValue = history[currentIndex];
  
  const setValue = useCallback((newValue) => {
    const value = typeof newValue === 'function' ? newValue(currentValue) : newValue;
    
    setHistory(prev => {
      const newHistory = prev.slice(0, currentIndex + 1);
      newHistory.push(value);
      
      // Limit history size
      if (newHistory.length > maxHistory) {
        newHistory.shift();
        return newHistory;
      }
      
      return newHistory;
    });
    
    setCurrentIndex(prev => Math.min(prev + 1, maxHistory - 1));
  }, [currentValue, currentIndex, maxHistory]);
  
  const undo = useCallback(() => {
    setCurrentIndex(prev => Math.max(0, prev - 1));
  }, []);
  
  const redo = useCallback(() => {
    setCurrentIndex(prev => Math.min(history.length - 1, prev + 1));
  }, [history.length]);
  
  const canUndo = currentIndex > 0;
  const canRedo = currentIndex < history.length - 1;
  
  return {
    value: currentValue,
    setValue,
    undo,
    redo,
    canUndo,
    canRedo,
    history: history.slice(0, currentIndex + 1)
  };
}

// 3. useAsyncState for handling async state updates
function useAsyncState(initialState) {
  const [state, setState] = useState(initialState);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  
  const setAsyncState = useCallback(async (asyncOperation) => {
    setLoading(true);
    setError(null);
    
    try {
      const result = await asyncOperation();
      setState(result);
      return result;
    } catch (err) {
      setError(err);
      throw err;
    } finally {
      setLoading(false);
    }
  }, []);
  
  return { state, loading, error, setAsyncState };
}

// Component using advanced patterns
function AdvancedPatternsDemo() {
  // State with history
  const {
    value: text,
    setValue: setText,
    undo,
    redo,
    canUndo,
    canRedo,
    history
  } = useStateWithHistory('');
  
  // Async state
  const { state: userData, loading, error, setAsyncState } = useAsyncState(null);
  
  // Reducer with middleware
  const [counterState, dispatch] = useReducerWithMiddleware(
    (state, action) => {
      switch (action.type) {
        case 'INCREMENT':
          return { count: state.count + 1 };
        case 'DECREMENT':
          return { count: state.count - 1 };
        default:
          return state;
      }
    },
    { count: 0 },
    [loggerMiddleware]
  );
  
  const fetchUserData = async () => {
    await setAsyncState(async () => {
      const response = await fetch('/api/user');
      return response.json();
    });
  };
  
  return (
    <div className="advanced-patterns-demo">
      <h2>Advanced Hook Patterns</h2>
      
      {/* State with history */}
      <div className="section">
        <h3>State with History</h3>
        <input
          value={text}
          onChange={(e) => setText(e.target.value)}
          placeholder="Type something..."
        />
        <div className="history-controls">
          <button onClick={undo} disabled={!canUndo}>
            Undo
          </button>
          <button onClick={redo} disabled={!canRedo}>
            Redo
          </button>
        </div>
        <div className="history-display">
          <h4>History:</h4>
          <ol>
            {history.map((item, index) => (
              <li key={index}>{item || '(empty)'}</li>
            ))}
          </ol>
        </div>
      </div>
      
      {/* Async state */}
      <div className="section">
        <h3>Async State</h3>
        <button onClick={fetchUserData} disabled={loading}>
          {loading ? 'Loading...' : 'Fetch User Data'}
        </button>
        {error && <p>Error: {error.message}</p>}
        {userData && <pre>{JSON.stringify(userData, null, 2)}</pre>}
      </div>
      
      {/* Reducer with middleware */}
      <div className="section">
        <h3>Reducer with Middleware</h3>
        <p>Count: {counterState.count}</p>
        <button onClick={() => dispatch({ type: 'INCREMENT' })}>
          Increment
        </button>
        <button onClick={() => dispatch({ type: 'DECREMENT' })}>
          Decrement
        </button>
        <p><small>Check console for middleware logs</small></p>
      </div>
    </div>
  );
}
```

**Interview Questions:**
1. When should you use useReducer instead of useState?
2. What are the different use cases for useRef?
3. How do you create and test custom hooks?
4. What is the difference between useMemo and useCallback?
5. How do you handle cleanup in custom hooks?
6. What are some common patterns for custom hooks?
7. How do you share logic between components using hooks?
8. What are the rules of hooks and why are they important?
9. How do you optimize performance with advanced hooks?
10. What are some advanced patterns for state management with hooks?

---### 🔹
 Day 39: Higher-Order Components (HOCs) - DEEP DIVE

**Definition (English):**
Higher-Order Components (HOCs) are functions that take a component and return a new component with additional functionality. They are a pattern for reusing component logic and were commonly used before hooks. HOCs follow the principle of composition over inheritance and allow for cross-cutting concerns like authentication, logging, and data fetching.

**Hinglish Deep Explanation:**
HOC ek advanced pattern hai jo component ko enhance karta hai. Ye ek function hota hai jo component leta hai aur enhanced component return karta hai. Hooks se pehle ye bahut popular tha logic reuse karne ke liye. Authentication, logging, data fetching jaise common functionalities ke liye use hota hai.

**HOC Deep Understanding:**

```jsx
// 1. Basic HOC Pattern
function withLoading(WrappedComponent) {
  return function WithLoadingComponent(props) {
    if (props.loading) {
      return <div className="loading">Loading...</div>;
    }
    
    return <WrappedComponent {...props} />;
  };
}

// Usage
const UserProfile = ({ user }) => (
  <div>
    <h2>{user.name}</h2>
    <p>{user.email}</p>
  </div>
);

const UserProfileWithLoading = withLoading(UserProfile);

// 2. HOC with Authentication
function withAuth(WrappedComponent, requiredRole = null) {
  return function WithAuthComponent(props) {
    const [user, setUser] = useState(null);
    const [loading, setLoading] = useState(true);
    
    useEffect(() => {
      // Check authentication
      const token = localStorage.getItem('authToken');
      if (token) {
        // Validate token and get user
        fetch('/api/auth/verify', {
          headers: { Authorization: `Bearer ${token}` }
        })
        .then(res => res.json())
        .then(userData => {
          setUser(userData);
          setLoading(false);
        })
        .catch(() => {
          setLoading(false);
        });
      } else {
        setLoading(false);
      }
    }, []);
    
    if (loading) {
      return <div>Checking authentication...</div>;
    }
    
    if (!user) {
      return <div>Please log in to access this page.</div>;
    }
    
    if (requiredRole && user.role !== requiredRole) {
      return <div>You don't have permission to access this page.</div>;
    }
    
    return <WrappedComponent {...props} user={user} />;
  };
}

// Usage
const AdminPanel = withAuth(({ user }) => (
  <div>
    <h2>Admin Panel</h2>
    <p>Welcome, {user.name}</p>
  </div>
), 'admin');

// 3. HOC for Data Fetching
function withData(WrappedComponent, dataSource) {
  return function WithDataComponent(props) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);
    
    useEffect(() => {
      const fetchData = async () => {
        try {
          setLoading(true);
          const response = await fetch(dataSource);
          if (!response.ok) throw new Error('Failed to fetch');
          const result = await response.json();
          setData(result);
        } catch (err) {
          setError(err.message);
        } finally {
          setLoading(false);
        }
      };
      
      fetchData();
    }, []);
    
    return (
      <WrappedComponent 
        {...props} 
        data={data} 
        loading={loading} 
        error={error} 
      />
    );
  };
}

// 4. Composing Multiple HOCs
const enhance = compose(
  withAuth,
  withLoading,
  withData('/api/users')
);

const EnhancedUserList = enhance(UserList);
```

### 🔹 Day 40: Render Props - DEEP DIVE

**Definition (English):**
Render Props is a pattern where a component receives a function as a prop that returns JSX. This function is called with data or functionality that the component provides, allowing for flexible and reusable component logic. It's an alternative to HOCs for sharing code between components.

**Hinglish Deep Explanation:**
Render Props ek pattern hai jisme component ko ek function prop milta hai jo JSX return karta hai. Ye function component ke data ke saath call hota hai, jisse flexible aur reusable logic ban jaata hai. Ye HOCs ka alternative hai code sharing ke liye.

```jsx
// 1. Basic Render Props Pattern
function MouseTracker({ render }) {
  const [position, setPosition] = useState({ x: 0, y: 0 });
  
  const handleMouseMove = (event) => {
    setPosition({
      x: event.clientX,
      y: event.clientY
    });
  };
  
  return (
    <div onMouseMove={handleMouseMove} style={{ height: '100vh' }}>
      {render(position)}
    </div>
  );
}

// Usage
function App() {
  return (
    <MouseTracker
      render={({ x, y }) => (
        <h2>Mouse position: ({x}, {y})</h2>
      )}
    />
  );
}

// 2. Data Fetcher with Render Props
function DataFetcher({ url, render }) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then(setData)
      .catch(setError)
      .finally(() => setLoading(false));
  }, [url]);
  
  return render({ data, loading, error });
}

// Usage
<DataFetcher
  url="/api/users"
  render={({ data, loading, error }) => {
    if (loading) return <div>Loading...</div>;
    if (error) return <div>Error: {error.message}</div>;
    return <UserList users={data} />;
  }}
/>
```

## 🎯 Final Summary and Best Practices

### React Development Best Practices:

**1. Component Design:**
- Keep components small and focused
- Use composition over inheritance
- Prefer functional components with hooks
- Implement proper prop validation

**2. State Management:**
- Use local state for component-specific data
- Use Context for app-wide state
- Consider Redux for complex state logic
- Avoid prop drilling

**3. Performance:**
- Use React.memo for expensive components
- Implement useMemo and useCallback wisely
- Use code splitting for large applications
- Optimize bundle sizes

**4. Testing:**
- Write tests for critical functionality
- Use React Testing Library
- Test user interactions, not implementation
- Mock external dependencies

**5. Code Organization:**
- Use consistent folder structure
- Separate concerns properly
- Create reusable custom hooks
- Follow naming conventions

### Key Takeaways:

✅ **Master the Fundamentals:** JSX, components, props, state, and event handling
✅ **Understand Hooks:** useState, useEffect, useContext, and custom hooks
✅ **Learn State Management:** Context API, Redux, and advanced patterns
✅ **Implement Routing:** React Router for navigation and protected routes
✅ **Optimize Performance:** Code splitting, memoization, and virtual scrolling
✅ **Write Tests:** Unit tests, integration tests, and E2E tests
✅ **Follow Best Practices:** Clean code, proper architecture, and maintainability

### Next Steps for Continued Learning:

1. **Build Projects:** Create real-world applications to practice concepts
2. **Explore Ecosystem:** Learn popular libraries and tools
3. **Stay Updated:** Follow React updates and new features
4. **Join Community:** Participate in React communities and forums
5. **Contribute:** Contribute to open-source React projects

---

*Congratulations! 🎉 You've completed a comprehensive deep-dive into React.js. Keep practicing, building projects, and staying curious. Happy coding!*

**Interview Questions:**
1. What are Higher-Order Components and when would you use them?
2. How do Render Props work and what problems do they solve?
3. What's the difference between HOCs and Render Props?
4. How do modern hooks compare to HOCs and Render Props?
5. What are some common patterns for code reuse in React?
6. How do you test components that use HOCs or Render Props?
7. What are the pros and cons of each pattern?
8. How do you compose multiple HOCs together?
9. What are some performance considerations with these patterns?
10. When should you choose hooks over HOCs or Render Props?

---
