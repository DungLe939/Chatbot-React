
## 1. Create Project With Vite

```terminal
npm create vite@latest
```


## 2. Simple Example React

```jsx
const div = (
	<div>
		<button>Click me</button>
		<p>This is a simple Text</p>
	</div>
);

const container = document.querySelector('.js-container');
ReactDOM.createRoot(container).render(div);
```

## 3. Insert code into Element

```jsx
const div = (
	<div>
		<button>Click me</button>
		<p>This is a simple Text number {3+1}</p>
	</div>
);

const container = document.querySelector('.js-container');
ReactDOM.createRoot(container).render(div);
```


## 4. Create a Component

```jsx
function ChatInput() {
            return (
                <div class="flex items-center gap-3 p-4 bg-white max-w-2xl">
                    <input
                        type="text"
                        placeholder="Send a message to Chatbot"
                        class="flex-1 px-4 py-3 border border-gray-400 rounded-lg outline-none text-gray-700 placeholder-gray-500 focus:border-green-600 transition-colors"
                    />

                    <button
                        class="bg-[#1a8754] hover:bg-[#156d43] text-white font-medium py-3 px-6 rounded-xl transition-all active:scale-95"
                    >
                        Send
                    </button>
                </div>
            );
```

## 5. Two step to trigger Component and Shortcut

```jsx
{ChatInput()}
<ChatInput> <ChatInput/>
<ChatInput/>
```

## 6. Fragment tag 

```jsx
<>
</>
```

## 7. Placeholder of the Input tag

```jsx
<input
    type="text"
    size="30"
	placeholder="Send a message to Chatbot"
/>
```


## 8. Works with img

```jsx
<img                 src="https://supersimple.dev/projects/chatbot/user.png"
alt="Avatar icon"
className="w-12 h-12 rounded-full"
/>
```

## 9. Attribute in Component (Props)

```jsx
function ChatMessage(props) {
    const text = props.message;
        return (
            <>
                {text}
                <img               src="https://supersimple.dev/projects/chatbot/user.png"
                    alt="Avatar icon"
                    className="w-12 h-12 rounded-full"
                />
            </>
        );
}

<ChatMessage message="This is a human message"/>
```

## 10. Shortcut to get Props (Destructuring)

```jsx
const {text, avatar} = props;
```

```jsx
function ChatMessage({ text, avatar }) {}
```

## 11. Guard Operator && Tenary Operation

```jsx
function ChatMessage({ text, avatar }) {
    return (
        <div className="flex items-center gap-3 p-4">
            {avatar === 'bot' && <img
                src={botAvatar}
                        alt="Bot Avatar icon"
                        className="w-12 h-12 rounded-full"
                    />}

                    {text}

                    {avatar === 'human' && <img
                        src={humanAvatar}
                        alt="Human Avatar icon"
                        className="w-12 h-12 rounded-full"
                    />}

                </div>
            );
        }
```


## 12. Store Data (Object) by Array list

```jsx
function App() {
    const chatMessage = [{
        message: 'Hello Bot',
        avatar: 'human'
    },{
    message: 'Hi user',
    avatar: 'bot'
}];
```

## 13. Map and Arrow Function

```jsx
const ChatMessageComponent = chatMessages.map((chatMessage) => {
    return (
        <>
            <ChatMessage 
                text={chatMessage.message} 
                avatar={chatMessage.avatar} 
            />
        </>
    );
});
```

## 14. Unique key problems

```jsx
function ChatMessageComponent() {
	const chatMessages = [{
		id: 'id1',
		message: 'Hello Bot',
		avatar: 'human'
	}, {
		id: 'id2',
		message: 'Hi user',
		avatar: 'bot'
	}, {
		id: 'id3',
		message: 'How can you help me?',
		avatar: 'human'
	}, {
		id: 'id4',
		message: 'I can assist with coding questions and more!',
		avatar: 'bot'
	}, {
		id: 'id5',
		message: 'That sounds great!',
		avatar: 'human'
	}, {
		id: 'id6',
		message: 'Feel free to ask me anything.',
		avatar: 'bot'
	}];

    return (
        chatMessages.map((chatMessage) => {
            return (
                <ChatMessage
                    key={chatMessage.id}
                    text={chatMessage.message}
                    avatar={chatMessage.avatar}
                />
            );
        })
    );
}
```


## 15. Event Handlers (onClick)

```jsx
onClick={() => {
	    chatMessages.push({
	    id: crypto.randomUUID(),
	    message: 'And there is full text',
	    avatar: 'bot'
    })
    console.log(chatMessages);
}}
```

## 16. State

```jsx
const [chatMessages, setChatMessages] = React.useState([{
	    id: 'id1',
	    message: 'Hello Bot',
	    avatar: 'human'
    }, {
        id: 'id2',
        message: 'Hi user',
        avatar: 'bot'
    }
]);
```

## 17. Spread Operator

- Copy tất cả các element sang mảng mới

```jsx
onClick={() => {
    setChatMessages([...chatMessages,
        {
            id: crypto.randomUUID(),
            message: 'And there is full text',
            avatar: 'bot'
        }
    ]);
}}
```


## 18. onChange

```jsx
<input
    type="text"
    placeholder="Send a message to Chatbot"
    onChange={(e) => {
        console.log(e.target.value);
    }}
/>
```


## 19. Lifting the state up

```jsx
function App() {
    const [chatMessages, setChatMessages] = React.useState([]);
        return (
            <>
	            <ChatInput chatMessages={chatMessages} setChatMessages={setChatMessages} />
	            <ChatMessageComponent chatMessages={chatMessages} />
            </>
    );
}
```


## 20. Name convention


## 21. Solve the reset when submit text (Controlled Input)

```jsx
<input
    type="text"
    placeholder="Send a message to Chatbot"
    value={inputText}
    onChange={ (e) => { setInputText(e.target.value); } }
/>

<button
    onClick={() => {
        setChatMessages([...chatMessages,
        {
            id: crypto.randomUUID(),
            message: inputText,
            avatar: 'human'
	    }
        ]);

        setInputText('');
    }}>
    Send
</button>
```


## 22. Baching

## 23. onKeyDown

```jsx
onKeyDown={(e) => {
    if(e.key === 'Enter')
        console.log("Enter active");
}}
```

## 24. Async and await

## 25. Callback

## 26. Closure

## 27. useEffect()

```jsx
React.useEffect(() => {
    console.log("hello");
}, [chatMessages]);
```

## 28. useRef()

```jsx
function ChatMessageComponent({ chatMessages }) {
    const chatMessageRef = React.useRef(null);

    React.useEffect(() => {
        if (chatMessageRef.current) {
	        chatMessageRef.current.scrollTop = chatMessageRef.current.scrollHeight;
        }}, [chatMessages]);

        return (
            <div
                ref={chatMessageRef}
	                className="flex-1 overflow-y-auto p-4 space-y-4 bg-gray-50"               >
                {chatMessages.map((message) => (
                    <ChatMessage
                        key={message.id}
                        text={message.message}
                        avatar={message.avatar}
                    />
                ))}
            </div>
        );
    }
```

