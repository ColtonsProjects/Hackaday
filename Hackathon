import { useState, useEffect } from 'react';
import './App.css';
import '@chatscope/chat-ui-kit-styles/dist/default/styles.min.css';
import {
  MainContainer,
  ChatContainer,
  MessageList,
  Message,
  MessageInput,
  TypingIndicator,
} from '@chatscope/chat-ui-kit-react';

const API_KEY = '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';

const systemMessage = {
  role: 'system',
  content:
    "Explain things like you're talking to a software professional with 2 years of experience.",
};

function App() {
  const [messages, setMessages] = useState([
    {
      message: 'Hello, Welcome to your virtual school assistant!',
      sentTime: 'just now',
      sender: 'ChatGPT',
    },
  ]);
  const [isTyping, setIsTyping] = useState(false);
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');
  const [courses, setCourses] = useState([]);
  const [selectedCourse, setSelectedCourse] = useState(null);

  useEffect(() => {
    // Fetch courses after successful login
    if (isLoggedIn) {
      fetchCourses();
    }
  }, [isLoggedIn]);

  async function fetchCourses() {
    // Fetch courses here using the Canvas API
    // This function should be implemented in the CanvasAPI.js file
    // and imported to use here.
  }

  const handleLogin = async (e) => {
    e.preventDefault();
    // Implement UCF SSO authentication and obtain an access token
    // Then set `isLoggedIn` to true.
  };

  const handleCourseSelection = (course) => {
    setSelectedCourse(course);
  };

  const handleSend = async (message) => {
    const newMessage = {
      message,
      direction: 'outgoing',
      sender: "user"
    }
  };

  // ... existing functions ...

  if (!isLoggedIn) {
    return (
      <div className="App">
        <form onSubmit={handleLogin}>
          <label>
            Canvas Username:
            <input
              type="text"
              value={username}
              onChange={(e) => setUsername(e.target.value)}
            />
          </label>
          <br />
          <label>
            Canvas Password:
            <input
              type="password"
              value={password}
              onChange={(e) => setPassword(e.target.value)}
            />
          </label>
          <br />
          <input type="submit" value="Log in" />
        </form>
      </div>
    );
  }

  if (!selectedCourse) {
    return (
      <div className="App">
        <h1>Select a course to discuss</h1>
        <ul>
          {courses.map((course) => (
            <li key={course.id} onClick={() => handleCourseSelection(course)}>
              {course.name}
            </li>
          ))}
        </ul>
      </div>
    );
  }

  return (
    <div className="App">
      <div style={{ position:"relative", height: "800px", width: "700px"  }}>
        <MainContainer>
          <ChatContainer>       
            <MessageList 
              scrollBehavior="smooth" 
              typingIndicator={isTyping ? <TypingIndicator content="ChatGPT is typing" /> : null}
            >
              {messages.map((message, i) => {
                console.log(message)
                return <Message key={i} model={message} />
              })}
            </MessageList>
            <MessageInput placeholder="Type message here" onSend={handleSend} />        
          </ChatContainer>
        </MainContainer>
      </div>
    </div>
  );
}

export default App;
