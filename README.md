# 🧠 Fun JS Challenge

> _To try out when you're bored — for JS lovers ❤️‍🩹_

No libraries. No shortcuts. Raw dot notation and bracket notation only. If you're reaching for `.find()` before you've mapped the shape in your head — start over.

---

## 📐 The Architecture

```
network
 ├── users
 │      └── [userId]
 │             ├── identity
 │             │      ├── username
 │             │      └── profile
 │             │             ├── public
 │             │             │      └── display { first, last }
 │             │             └── private
 │             │                    └── settings
 │             │                           └── theme { current }
 │             ├── social
 │             │      └── followers
 │             │             ├── active   [ ...userIds ]
 │             │             └── inactive [ ...userIds ]
 │             └── memories
 │                    └── ai
 │                           └── rivals
 │                                  ├── primary   [ ...userIds ]
 │                                  └── secondary [ ...userIds ]
 ├── relations
 ├── communities
 ├── posts
 │      └── [postId]
 │             ├── author  (userId string)
 │             ├── content
 │             │      └── body { text }
 │             ├── analytics
 │             │      └── impressions
 │             │             ├── hourly  [ ...numbers ]
 │             │             └── total   (number)
 │             ├── engagement
 │             │      ├── likes
 │             │      │      └── users  [ ...userIds ]
 │             │      ├── reactions
 │             │      │      ├── laugh  [ ...userIds ]
 │             │      │      ├── angry  [ ...userIds ]
 │             │      │      └── fire   [ ...userIds ]
 │             │      └── comments
 │             │             └── [commentId]
 │             │                    ├── author  (userId string)
 │             │                    ├── payload { text }
 │             │                    └── replies
 │             │                           └── [replyId]
 │             │                                  ├── author  (userId string)
 │             │                                  └── payload { text }
 │             └── metadata
 └── aiMemory
```

---

## 🧬 The Data

```js
const hive = {
  network: {
    users: {
      u001: {
        identity: {
          username: "trebo",
          profile: {
            public: {
              display: {
                first: "Trebo",
                last: "King"
              }
            },
            private: {
              settings: {
                theme: {
                  current: "dark"
                }
              }
            }
          }
        },
        social: {
          followers: {
            active: ["u002", "u004"],
            inactive: ["u007"]
          }
        },
        memories: {
          ai: {
            rivals: {
              primary: ["u003"],
              secondary: ["u008"]
            }
          }
        }
      },
      u002: { identity: { username: "drake" } },
      u003: { identity: { username: "israel" } },
      u004: { identity: { username: "sarah" } },
      u005: { identity: { username: "mike" } },
      u006: { identity: { username: "zara" } },
      u007: { identity: { username: "ghost" } },
      u008: { identity: { username: "nova" } }
    },

    posts: {
      p001: {
        author: "u001",
        content: {
          body: {
            text: "React is overrated"
          }
        },
        analytics: {
          impressions: {
            hourly: [23, 44, 12],
            total: 79
          }
        },
        engagement: {
          likes: {
            users: ["u002", "u003", "u005"]
          },
          reactions: {
            laugh: ["u004"],
            angry: ["u007"],
            fire:  ["u008"]
          },
          comments: {
            c001: {
              author: "u003",
              payload: {
                text: "Worst take"
              },
              replies: {
                r001: {
                  author: "u002",
                  payload: { text: "Skill issue" }
                },
                r002: {
                  author: "u008",
                  payload: { text: "Cook again" }
                }
              }
            }
          }
        }
      }
    }
  }
}
```

---

## 😈 The Questions

Work them in order. Each one is harder than it looks.

---

### Tier 1 — Warm Up (Don't get comfortable)

**1.** Get the 3rd letter in Trebo's username.

**2.** Get the last letter in Drake's username.

**3.** Get Trebo's current theme.

**4.** Get Trebo's second rival. _(primary or secondary? figure it out)_

**5.** Get the first inactive follower of Trebo.

---

### Tier 2 — Going Deeper

**6.** Get total impressions on `p001`.

**7.** Get the first user that liked `p001`.

**8.** Get the last user that liked `p001`.

**9.** Get the number of likes on `p001`.

**10.** Get the first angry reaction user.

**11.** Get the second hourly impression value.

**12.** Get the text of the first comment.

**13.** Get the text of the first reply.

**14.** Get the author of the second reply.

**15.** Get the username of user `u008`.

---

### Tier 3 — Now You're Working

**16.** Get the first **word** of comment `c001`'s text. _(string method required)_

**17.** Count the total number of individual reaction entries across all reaction types on `p001`.

**18.** Count the total number of replies on `c001`.

**19.** Get the last character of Nova's username. _(resolve the id first, then dig)_

**20.** Get the username of whoever authored `p001`.

---

### Tier 4 — Multi-Step Lookups (This is where people tab out)

**21.** Return an array of **every userId** that reacted to `p001` (any reaction type).

**22.** Return an array of **every userId** that commented on `p001`.

**23.** Return an array of **every userId** that replied on any comment in `p001`.

**24.** Return a flat array of **all rivals** of Trebo (primary + secondary combined).

**25.** Count the **total engagement** on `p001`: likes + all reactions + comments + replies.

---

### Tier 5 — Boss Level (You better loop)

**26.** Find the user with the most social connections. _(active + inactive followers combined, highest count wins)_

**27.** Return an array of **all usernames** in the network.

**28.** Return an array of **all post IDs** in the network.

**29.** Return an array of **all comment IDs** inside `p001`.

**30.** Return an array of **all reply IDs** across all comments in `p001`.

---

## 🔒 Rules

- No external libraries
- No `JSON.stringify` tricks
- Dot notation and bracket notation only — pick what the key demands
- For dynamic keys (`u001`, `p001`, `c001`), ask yourself: _why bracket notation?_
- Questions 21–30 require `Object.keys()` — learn it before you try them

---

## 💡 Concepts This Drills

| Concept | Questions |
|---|---|
| Deep nested property access | 1, 3, 4, 6, 12, 13 |
| String indexing | 1, 2, 19 |
| Array indexing | 5, 7, 8, 10, 11, 14 |
| `.length` on arrays/strings | 2, 9, 17, 18 |
| Dynamic bracket key access | 4, 15, 20 |
| String methods (`.split()`) | 16 |
| `Object.keys()` + iteration | 21–30 |
| Multi-step resolution (id → object → property) | 15, 19, 20 |
| Combining arrays | 21, 24 |
| Counting nested values | 17, 18, 25 |
| Looping object entries | 26, 27, 28, 29, 30 |

---

## ✅ Answers

DM **+2349161712483** for the answers 👀
