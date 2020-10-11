
# Create Course
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Delete
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> id2.2{Is a teacher?};
    id2.2 -->|yes| fill2[Delete course];
    id2.2 -->|No| exit2;
    fill2 --> exit2
end

subgraph Edit
    start1["#cir;"]:::points
    exit1["#bull;"]:::points

    start1 --> id2.1{Is a teacher or TA?};
    id2.1 -->|yes| fill1[Fill in new course info];
    id2.1 -->|No| exit1;
    fill1 --> fill11[Edit a grade category and its weight]
    fill11 --> sub1[Submit new info];
    sub1 --> exit1
end
```
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px
subgraph Create
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> id2{Is a teacher?};
    id2 -->|yes| fill[Fill in Course info];
    id2 -->|No| exit;
    fill --> fill22{Add a grading category?}

    fill22 --> |Yes| g[Add category name and weight]
    g --> fill22
    fill22 --> |No| sub[Submit course creation];
    sub --> exit
end
```

# Editing TA
```mermaid
graph TD
    classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> id{Is a teacher?}
    id --> |No| exit
    id --> |Yes| v[View all student]
    v --> sel{Select a student?}

    sel --> |No| exit
    sel --> |Yes| se[Select a student]
    se --> c["Change student's TA status from 'false to true' or 'true to false'"]
    c --> s[save]
    s --> sel
    s --> exit
```

# Account Authentication
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, , font-size:30px

subgraph Login
    start1["#cir;"]:::points
    exit1["#bull;"]:::points

    start1 --> l[Had login ?]
    l --> |yes| exit1
    l --> |No| ll[Login with Canvas]
    ll --> r[Redirect to homepage]
    r --> exit1
end

subgraph Logout
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> l1{Login ?}
    l1 --> |No| exit2
    l1 --> |Yes| l2[Logout]
    l2 --> r2[Redirect to homepage]
    r2 --> exit2
end
```

# Create Assignments, Tests, or Quizzes
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Create
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> id2{Is a teacher or TA?};
    id2 -->|yes| fill["Fill in title and description (open/close/due dates)"];
    fill --> f2["Assign a grade category (Assignment, Test, Quiz,...)"]
    f2 --> q{Add a question?}
    id2 --> |No| exit

    q --> |Yes| q1[Create a question and assign points]
    q1 --> m{miltiple choice?}
    m --> |Yes| a[Create answers]
    a --> q
    m --> |No| q

    q --> |No| sub["Upload an answer pdf (optional)"]
    sub --> sub2[Submit creation]
    sub2 --> exit
end
```

```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Delete
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> is2{Is a teacher or TA?};
    is2 --> |Yes| ex2{Assignment exist?}
    is2 --> |No| exit2

    ex2 --> d[Delete the assignment and all of its related data]
    d --> exit2
end

subgraph Edit
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> id2{Is a teacher or TA?};
    id2 --> |Yes| ex{Assignment exist?}
    id2 --> |No| exit

    ex --> |Yes| q["Edit title and description (open/close/due dates)"]
    q --> q2{Choose a question to edit?}
    q2 --> |Yes| q3[Edit question and its answers]
    q3 --> q2
    ex --> |No| exit

    q2 --> |No| q4{Re-upload answers pdf?}
    q4 --> |Yes| up[Upload PDF]
    q4 --> |No| st{Change status to visible?}
    up --> st

    st --> |Yes| stt[Change status to visible to student]
    st --> |No| s[Save Changes]
    stt --> s

    s --> exit 
end
```

# Grading
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Assign points to an assignment
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> id[Is a teacher or TA?]
    id --> |No| exit
    id --> |Yes| a{Assignment exist?}

    a --> |No| exit
    a --> |Yes| v[View all students and their grade for that assignment]
    
    v --> sel{Select a student?}
    sel --> |No| exit
    sel --> |Yes| va[View student's answers]
    va --> as[Assign a grade]
    as --> save
    save --> sel
end

subgraph View Grade
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> id2[Is a teacher or TA?]
    id2 --> |No| g2{Student exist in course?}
    id2 --> |Yes| v2[View all students]
    
    v2 --> sel2{Select a student?}
    sel2 --> |No| exit2
    sel2 --> |Yes| va2[View student's grade]
    va2 --> sel2

    g2 --> |yes| g3[View student grade]
    g3 --> exit2
    g2 --> |No| exit2
end
```

# Discussion
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Create a discussion
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> id{Enroll in course?}
    id --> |No| exit
    id --> |Yes| a[Add title and comments]
    a --> submit --> exit
end

subgraph Reply to a discussion
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> id2{Enroll in course?}
    id2 --> |No| exit2
    id2 --> |Yes| d2{Discussion exist?}

    d2 --> |No| exit2
    d2 --> |Yes| w2[Write comments]
    w2 --> sub2[Submit] --> exit2
end

subgraph Delete a discussion
    start3["#cir;"]:::points
    exit3["#bull;"]:::points

    start3 --> id3{Enroll in course?}
    id3 --> |No| exit3
    id3 --> |Yes| d3{Discussion exist?}

    d3 --> |No| exit3
    d3 --> |Yes| idd3{Is owner or TA or teacher?}

    idd3 --> |No| exit3
    idd3 --> |Yes| dd3[Delete discussion and all of its related data]
    dd3 --> exit3
end
```
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Edit discussion
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> id{Enroll in course?}
    id --> |No| exit
    id --> |Yes| d{Discussion exist?}

    d --> |No| exit
    d --> |Yes| ed[Edit comments or title]
    ed --> Save --> exit
end

subgraph Edit reply
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> id2{Enroll in course?}
    id2 --> |No| exit2
    id2 --> |Yes| d2{Reply exist?}

    d2 --> |No| exit2
    d2 --> |Yes| ed2[Edit comments]
    ed2 --> save2[Save] --> exit2
end
```

# Inbox
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> s{Sender's email exist in the database and belong to the account?}
    s --> |No| exit
    s --> |Yes| reply{Reply to an email thread?}

    reply --> |No| w[Write messages and upload files]
    reply --> |Yes| att[Attach previous email threads]
    att --> w --> Save
    Save --> send{Send ?}

    send --> |Yes| sc[Send] --> exit
    send --> |No| sc2[Save as draft] --> exit
```

## Chatbox
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Reply in a Chatbox
    start3["#cir;"]:::points
    exit3["#bull;"]:::points
    start3 --> vr3{"Account is registered to the correct Chatbox?"}

    vr3 --> |No| exit3
    vr3 --> |Yes| re[Type a reply] --> send{Send?}
    send --> |No| exit3
    send --> |Yes| Send --> exit3
end

subgraph Create a Chatbox
    start["#cir;"]:::points
    exit["#bull;"]:::points
    start --> vr{Host's account is registered to the course?}
    vr --> |No| exit
    vr --> |Yes| cr[Create chatbox and register it to the course]
    cr --> hs[Add host to chatbox] --> exit
end

subgraph Delete a Chatbox
    start2["#cir;"]:::points
    exit2["#bull;"]:::points
    start2 --> vr2{"Account belong to host account (creator account)?"}
    vr2 --> |No| exit2
    vr2 --> |Yes| Delete --> exit2
end
```

```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Add a member in Chatbox
    start["#cir;"]:::points
    exit["#bull;"]:::points
    start --> vr{Account is registered to the correct Chatbox?}
    vr --> |No| exit
    vr --> |Yes| show[View all members of course]
    show --> hs{Choose a person?}
    hs --> |Yes| hss{Person registered to course?}
    hs --> |No| exit
    hss --> |No| show
    hss --> |Yes| add[Add person]
    add --> Save --> exit
end

subgraph Remove a member in Chatbox
    start2["#cir;"]:::points
    exit2["#bull;"]:::points
    start2 --> vr2{Account is registered to the correct Chatbox?}
    vr2 --> |No| exit2
    vr2 --> |Yes| show2[View all members of Chatbox]
    show2 --> hs2{Choose a person?}
    
    hs2 --> |Yes| hss2{Person is the owner?}
    hs2 --> |No| exit2

    hss2 --> |Yes| exit2
    hss2 --> |No| rem[Remove person]
    rem --> save2[Save] --> exit2
end
```

## Profile
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Edit Profile
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> vr{"Valid JSON Web Token (JWT)?"}
    vr --> |No| Logout --> exit
    vr --> |Yes| edit[Edit Nickname and Bio]
    edit --> c[Add preferable email contacts]
    c --> pf[Change Profile Picture]
    pf --> s{Save ?}
    s --> |No| exit
    s --> |Yes| Save
    Save --> exit
end

subgraph Change Settings
    start1["#cir;"]:::points
    exit1["#bull;"]:::points

    start1 --> vr1{"Valid JSON Web Token (JWT)?"}
    vr1 --> |No| Logout1[Logout] --> exit1
    vr1 --> |Yes| c1[On/Off Emailing Inboxes Notification]
    c1 --> c1.1[On/Off Emailing Calendar Notification]
    c1.1 --> c1.2[On/Off Emailing Assignment due dates Notification]
    c1.2 --> c1.3[On/Off Emailing Grading Notification]
    c1.3 --> c1.4[On/Off Emailing To-do-list Notification]
    c1.4 --> c2[Add github account]
    c2 --> c3[Add google drive account]
    c3 --> c4[Change dashboard color theme]
    c4 --> c5[Change Fontsize]
    c5 --> s2[Save] --> exit1
end
```

## Announcement
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Create Announcement
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> vr{Is TA or Teacher of course?}
    vr --> |No| exit
    vr --> |Yes| wr[Write Announcement]
    wr --> send{Send ?}
    send --> |No| exit
    send --> |Yes| Send --> exit
end

subgraph Edit Announcement
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> vr2{Is TA or Teacher of course?}
    vr2 --> |No| exit2
    vr2 --> |Yes| ex[Is announcement exist?]

    ex --> |No| exit2

    ex --> |Yes| wr2[Edit Announcement]
    wr2 --> send2{Send ?}
    send2 --> |No| exit2
    send2 --> |Yes| zz[Send] --> exit2
end

subgraph Delete Announcement
    start3["#cir;"]:::points
    exit3["#bull;"]:::points

    start3 --> vr3{Is TA or Teacher of course?}
    vr3 --> |No| exit3
    vr3 --> |Yes| ex3[Is announcement exist?]

    ex3 --> |No| exit3

    ex3 --> |Yes| send3{Delete ?}
    send3 --> |No| exit3
    send3 --> |Yes| zz3[Delete] --> exit3
end
```

## Calendar
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Create Calendar Event
    start["#cir;"]:::points
    exit["#bull;"]:::points
    
    start --> vr{TA or Teacher?}

    vr --> |"No (then they are student)"| cs["Choose Invitees (only individuals emails)"]
    vr --> |Yes| sel{Select a course?}
    sel --> |Yes| c["Choose Invitees (all students of course and individual emails)"]
    sel --> |No| cc["Choose Invitees (only individual emails)"]

    c --> fill[Fill in title, meeting links, description, and dates]
    cs --> fill
    cc --> fill

    fill --> s{Send ?}
    s--> |No| exit
    s--> |Yes| Send --> exit
end
```
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Edit Event
    start["#cir;"]:::points
    exit["#bull;"]:::points
    
    start --> sel{Select an event}
    sel --> vr{"is event's creator?"}
    vr --> |No| exit
    vr --> |Yes| cha[Change title, meeting links, description, and dates]
    cha --> s{Save ?}
    s --> |No| exit
    s --> |Yes| Save --> exit
end

subgraph Delete Event
    start2["#cir;"]:::points
    exit2["#bull;"]:::points
    
    start2 --> sel2{Select an event}
    sel2 --> vr2{"is event's creator?"}
    vr2 --> |No| exit2
    vr2 --> |Yes| s2{Delete ?}
    s2 --> |No| exit2
    s2 --> |Yes| Delete --> exit2
end
```

## To-do list
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Create To-Do Item
    start["#cir;"]:::points
    exit["#bull;"]:::points
    
    start --> vr{User account exist?}
    vr --> |No| exit
    vr --> |Yes| ch["Choose a due date (current date as default)"]
    ch --> wr[Write some notes]
    wr --> Save --> exit
end

subgraph Mark To-Do Item
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> ch2{"To-do item belong to user?"}
    ch2 --> |No| exit2
    ch2 --> |Yes| mk["Mark as `done` or `not done`"]
    mk --> s2[Save] --> exit2
end
```
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Edit To-Do Item
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> vr{"To-do item belong to user?"}
    vr --> |No| exit
    vr --> |Yes| ed[Edit item contents and date]
    ed --> Save --> exit
end

subgraph Delete To-Do Item
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> vr2{"To-do item belong to user?"}
    vr2 --> |No| exit2
    vr2 --> |Yes| Delete --> exit2
end
```

## Notes
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Create Notes
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> us[User create a note]
    us --> date["Choose a date (default on current date)"]
    date --> c{Choose a course for the note?}
    
    c--> |No| wr[Write some notes]
    c--> |Yes| rg[Register notes to course for easy access] --> wr
    wr --> Save --> exit
end

subgraph Edit Notes
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> vr{Selected note belong to user?}
    vr --> |No| exit2
    vr --> |Yes| edit[Edit notes and dates]
    edit --> s2[Save] --> exit2
end

subgraph Delete Notes
    start3["#cir;"]:::points
    exit3["#bull;"]:::points

    start3 --> vr3{Selected note belong to user?}
    vr3 --> |No| exit3
    vr3 --> |Yes| Delete --> exit3
end
```

## Personalize Dashboard
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Move Dashboard Item
    start["#cir;"]:::points
    exit["#bull;"]:::points

    start --> vr{Verified JWT?}
    vr --> |No| lg1[Logout] --> exit
    vr --> |Yes| ed[go to Edit mode] --> mv[Move items on dashboard to desired location]
    mv --> Save --> exit
end

subgraph Show/Hide Dashboard Item
    start2["#cir;"]:::points
    exit2["#bull;"]:::points

    start2 --> vr2{Verified JWT?}
    vr2 --> |No| lg[Logout] --> exit2
    vr2 --> ed2[go to Edit mode] --> shw[Show Items Window] --> sh[Show/Hide items]
    sh --> s3[Save] --> exit2
end

subgraph Resize Dashboard Item
    start3["#cir;"]:::points
    exit3["#bull;"]:::points

    start3 --> vr3{Verified JWT?}
    vr3 --> |No| lg4[Logout] --> exit3
    vr3 --> ed3[go to Edit mode] --> rz[Drag at corner to resize items on dashboard]
    rz --> s2[Save] --> exit3
end
```