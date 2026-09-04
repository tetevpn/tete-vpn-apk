<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🐼 برنامه‌ریز پاندایی</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Vazir', 'Comic Sans MS', system-ui, sans-serif;
        }

        html, body {
            height: 100%;
            overflow: hidden;
        }

        body {
            background: linear-gradient(145deg, #1a0f1a, #2d1a2d);
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 8px;
        }

        .container {
            max-width: 780px;
            width: 100%;
            height: 94vh;
            max-height: 580px;
            background: #ffedf5;
            background-image: radial-gradient(circle at 10% 20%, #ffe8f0 0%, #ffd6e6 100%);
            border-radius: 40px 40px 32px 32px;
            padding: 14px 18px 12px;
            box-shadow: 0 16px 32px rgba(0, 0, 0, 0.6), 0 0 0 3px #ffb6d9, 0 0 0 6px #ff8ec4;
            border: 2px solid #ffa5c8;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
        }

        /* هدر */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: nowrap;
            gap: 8px;
            background: rgba(255, 215, 235, 0.5);
            backdrop-filter: blur(4px);
            padding: 4px 14px 4px 10px;
            border-radius: 100px;
            border: 2px solid #ffb0d0;
            box-shadow: 0 3px 0 #d47a9e;
            flex-shrink: 0;
        }

        .header .greeting {
            display: flex;
            align-items: center;
            gap: 6px;
            flex: 1;
            min-width: 0;
        }

        .header .greeting .panda-icon {
            font-size: 26px;
            filter: drop-shadow(0 3px 5px #d47a9e);
            flex-shrink: 0;
            cursor: pointer;
            transition: 0.2s;
            position: relative;
            z-index: 5;
        }

        .header .greeting .panda-icon:hover {
            transform: scale(1.1) rotate(-5deg);
        }

        .header .greeting input {
            background: #fff0f7;
            border: 2px solid #ffa5c8;
            border-radius: 60px;
            padding: 4px 14px;
            font-size: 13px;
            font-weight: 500;
            color: #3d1f31;
            width: 100%;
            min-width: 60px;
            outline: none;
            box-shadow: inset 0 2px 6px #ffc1d9;
            transition: 0.2s;
        }

        .header .greeting input:focus {
            border-color: #ff6b9d;
            box-shadow: 0 0 0 4px #ffb0d0, inset 0 2px 6px #ff8eb5;
        }

        .header .date-badge {
            background: #ffd9e8;
            padding: 4px 14px;
            border-radius: 60px;
            border: 2px solid #ff8eb5;
            font-weight: 600;
            color: #591d3f;
            display: flex;
            align-items: center;
            gap: 6px;
            box-shadow: 0 3px 0 #bf6f8f;
            font-size: 12px;
            white-space: nowrap;
            flex-shrink: 0;
        }

        .header .date-badge i {
            color: #d45a86;
        }

        /* افزودن عادت */
        .add-habit {
            background: #ffdcec;
            border-radius: 60px;
            padding: 6px 14px;
            margin: 8px 0 10px;
            border: 2px solid #ff8eb5;
            display: flex;
            flex-wrap: nowrap;
            align-items: center;
            gap: 8px;
            box-shadow: 0 3px 0 #c46e8f;
            flex-shrink: 0;
        }

        .add-habit input {
            flex: 1;
            min-width: 50px;
            background: #fff5fa;
            border: 2px solid #ffa5c8;
            padding: 6px 14px;
            border-radius: 60px;
            color: #331d2a;
            font-size: 12px;
            outline: none;
            box-shadow: inset 0 2px 6px #ffc1d9;
            transition: 0.2s;
        }

        .add-habit input:focus {
            border-color: #ff5890;
            box-shadow: 0 0 0 4px #ffb0d0, inset 0 2px 6px #ff8eb5;
        }

        .add-habit .btn-add {
            background: #ff7aa8;
            border: none;
            padding: 6px 16px;
            border-radius: 60px;
            color: #fff5f9;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 6px;
            cursor: pointer;
            transition: 0.15s;
            border: 2px solid #ff4d82;
            box-shadow: 0 3px 0 #b15379;
            font-size: 12px;
            white-space: nowrap;
            flex-shrink: 0;
        }

        .add-habit .btn-add:hover {
            transform: translateY(-2px);
            background: #ff6b9d;
            box-shadow: 0 5px 0 #b15379;
        }

        .add-habit .btn-add:active {
            transform: translateY(2px);
            box-shadow: 0 2px 0 #b15379;
        }

        /* جدول عادات */
        .habits-wrapper {
            background: #ffecf3;
            border-radius: 24px;
            padding: 4px 4px 4px 6px;
            border: 2px solid #ff8eb5;
            margin: 4px 0 8px;
            overflow-x: auto;
            box-shadow: inset 0 0 0 3px #ffd0e3, 0 4px 0 #b86989;
            flex: 1;
            min-height: 0;
            -webkit-overflow-scrolling: touch;
        }

        .habits-table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0 3px;
            font-size: 12px;
            min-width: 380px;
        }

        .habits-table th {
            text-align: center;
            padding: 4px 2px 3px;
            color: #592642;
            font-weight: 600;
            font-size: 11px;
            background: #ffd0e3;
            border-radius: 16px 16px 0 0;
            border-bottom: 2px solid #ff8eb5;
        }

        .habits-table td {
            text-align: center;
            padding: 3px 2px;
            vertical-align: middle;
            background: rgba(255, 245, 248, 0.4);
            border-radius: 12px;
        }

        .habit-label-cell {
            display: flex;
            align-items: center;
            gap: 4px;
            padding: 2px 6px 2px 3px;
            background: #ffecf3;
            border-radius: 60px;
            border: 2px solid #ffb0d0;
            box-shadow: inset 0 2px 4px #ffc1d9;
            min-width: 80px;
        }

        .habit-label-cell i {
            color: #d45a86;
            font-size: 13px;
            width: 20px;
            text-align: center;
            flex-shrink: 0;
        }

        .habit-label-cell .habit-text {
            background: transparent;
            border: none;
            color: #331d2a;
            font-size: 12px;
            padding: 2px 2px;
            width: 80px;
            outline: none;
            font-weight: 500;
            border-bottom: 2px dashed #ff8eb5;
            transition: 0.2s;
        }

        .habit-label-cell .habit-text:focus {
            border-bottom-color: #ff4d82;
            color: #1f0d17;
        }

        .habit-label-cell .habit-text::placeholder {
            color: #b06a86;
            font-weight: 300;
            font-size: 11px;
        }

        /* چک‌باکس کوچک‌تر */
        .check-box {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 24px;
            height: 24px;
            background: #fff0f7;
            border-radius: 50%;
            border: 2.5px solid #ff8eb5;
            color: #d45a86;
            cursor: pointer;
            transition: 0.12s;
            font-size: 11px;
            box-shadow: 0 2px 0 #b86989, 0 2px 4px rgba(0,0,0,0.1);
        }

        .check-box.filled {
            background: #ff7aa8;
            border-color: #ff4d82;
            color: #fff5f9;
            box-shadow: 0 2px 0 #b15379, 0 0 8px #ff7aa877;
            transform: scale(0.92);
        }

        .check-box i {
            pointer-events: none;
            filter: drop-shadow(0 1px 2px rgba(0,0,0,0.1));
        }

        .delete-habit {
            background: #ffdcec;
            border: 2px solid #ff8eb5;
            color: #b15379;
            cursor: pointer;
            font-size: 11px;
            padding: 2px 10px;
            border-radius: 60px;
            transition: 0.2s;
            box-shadow: 0 2px 0 #b86989;
            font-weight: bold;
        }

        .delete-habit:hover {
            background: #ffb0d0;
            color: #591d3f;
            transform: scale(1.05);
        }

        /* پیشرفت هفتگی */
        .weekly-progress {
            background: #ffdcec;
            border-radius: 60px;
            padding: 6px 14px;
            margin: 4px 0 8px;
            border: 2px solid #ff8eb5;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: nowrap;
            gap: 8px;
            box-shadow: 0 3px 0 #b86989;
            flex-shrink: 0;
        }

        .weekly-progress .label {
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 12px;
            font-weight: 600;
            color: #3d1f31;
            white-space: nowrap;
        }

        .weekly-progress .label i {
            color: #d45a86;
            font-size: 16px;
        }

        .stats {
            display: flex;
            gap: 8px;
            flex-wrap: nowrap;
        }

        .stats .stat-item {
            display: flex;
            align-items: center;
            gap: 4px;
            background: #fff0f7;
            padding: 3px 10px 3px 8px;
            border-radius: 60px;
            border: 2px solid #ffa5c8;
            font-weight: 500;
            font-size: 11px;
            box-shadow: 0 2px 0 #b86989;
            white-space: nowrap;
        }

        .stats .stat-item.done i {
            color: #3bb08b;
        }

        .stats .stat-item.undone i {
            color: #e86868;
        }

        .stats .stat-item .num {
            font-weight: 700;
            color: #2e1a2a;
            font-size: 14px;
            margin-right: 2px;
        }

        /* فوتر */
        .footer {
            display: flex;
            justify-content: center;
            align-items: center;
            padding-top: 4px;
            border-top: 2px solid #ffb0d0;
            color: #592642;
            font-weight: 500;
            flex-shrink: 0;
            font-size: 11px;
            gap: 4px;
        }

        .footer i {
            color: #d45a86;
        }

        /* نوار عددی با برچسب انجام نشد / انجام شد */
        .progress-strip {
            display: flex;
            gap: 3px;
            justify-content: center;
            padding-top: 4px;
            border-top: 2px solid #ffb0d0;
            flex-wrap: nowrap;
            color: #592642;
            font-weight: 600;
            font-size: 11px;
            flex-shrink: 0;
            margin-top: 3px;
            align-items: center;
        }

        .progress-strip .status-label {
            background: #ffdcec;
            padding: 2px 10px;
            border-radius: 60px;
            border: 2px solid #ff8eb5;
            box-shadow: 0 2px 0 #b86989;
            font-size: 10px;
        }

        .progress-strip .status-label.done {
            background: #ff7aa8;
            color: #fff5f9;
            border-color: #ff4d82;
            box-shadow: 0 2px 0 #b15379;
        }

        .progress-strip .panda-badge {
            background: #ffb0d0;
            border-color: #ff4d82;
            padding: 2px 8px;
        }

        .habits-wrapper::-webkit-scrollbar {
            height: 5px;
        }
        .habits-wrapper::-webkit-scrollbar-track {
            background: #ffd0e3;
            border-radius: 30px;
        }
        .habits-wrapper::-webkit-scrollbar-thumb {
            background: #ff8eb5;
            border-radius: 30px;
            border: 2px solid #ffb0d0;
        }

        /* مدال پاندا */
        .panda-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            background: rgba(0,0,0,0.3);
            backdrop-filter: blur(4px);
            animation: fadeIn 0.3s ease;
        }

        .panda-modal.active {
            display: flex;
        }

        .panda-modal .modal-content {
            position: relative;
            max-width: 360px;
            width: 90%;
            border-radius: 40px;
            overflow: hidden;
            box-shadow: 0 30px 60px rgba(0,0,0,0.6);
            border: 4px solid #ff8ec4;
            animation: popIn 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
        }

        .panda-modal .modal-content img {
            width: 100%;
            height: auto;
            display: block;
            border-radius: 36px;
        }

        .panda-modal .emoji-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
            border-radius: 36px;
        }

        .panda-modal .emoji-overlay span {
            position: absolute;
            font-size: 28px;
            animation: floatEmoji 1.8s ease-out forwards;
            opacity: 0;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes popIn {
            0% { transform: scale(0.7); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        @keyframes floatEmoji {
            0% { transform: translateY(0) scale(0.3); opacity: 0; }
            20% { opacity: 0.9; transform: translateY(-10px) scale(1); }
            100% { transform: translateY(-120px) scale(0.6); opacity: 0; }
        }

        @media (max-width: 650px) {
            .container { padding: 10px; max-height: 98vh; max-width: 100%; }
            .header .greeting input { font-size: 11px; padding: 3px 10px; }
            .header .date-badge { font-size: 10px; padding: 3px 10px; }
            .add-habit input { font-size: 11px; padding: 4px 10px; }
            .add-habit .btn-add { font-size: 11px; padding: 4px 12px; }
            .habits-table { font-size: 11px; min-width: 340px; }
            .habit-label-cell .habit-text { width: 60px; font-size: 11px; }
            .check-box { width: 22px; height: 22px; font-size: 10px; }
            .weekly-progress .label { font-size: 11px; }
            .stats .stat-item { font-size: 10px; padding: 2px 8px; }
            .footer { font-size: 10px; }
            .progress-strip { font-size: 10px; }
            .progress-strip span { padding: 1px 8px; }
        }
    </style>
</head>
<body>

<div class="container">

    <!-- هدر -->
    <div class="header">
        <div class="greeting">
            <span class="panda-icon" id="pandaTrigger">🐼</span>
            <input type="text" placeholder="هدف امروزت..." id="userGoal">
        </div>
        <div class="date-badge">
            <i class="fas fa-calendar-alt"></i> مرداد ۱۴۰۵
        </div>
    </div>

    <!-- افزودن عادت -->
    <div class="add-habit">
        <input type="text" id="newHabitInput" placeholder="مثلا: ۳۰ دقیقه یوگا 🧘" />
        <button class="btn-add" id="addHabitBtn"><i class="fas fa-paw"></i> افزودن</button>
    </div>

    <!-- جدول عادات -->
    <div class="habits-wrapper">
        <table class="habits-table" id="habitsTable">
            <thead>
                <tr>
                    <th style="text-align:right; border-radius: 16px 0 0 0;">🐼 عادت</th>
                    <th>۱</th>
                    <th>۲</th>
                    <th>۳</th>
                    <th>۴</th>
                    <th>۵</th>
                    <th>۶</th>
                    <th>۷</th>
                    <th style="border-radius: 0 16px 0 0;">🗑️</th>
                </tr>
            </thead>
            <tbody id="habitsBody">
                <!-- ردیف‌ها توسط JS ساخته می‌شوند -->
            </tbody>
        </table>
    </div>

    <!-- پیشرفت هفتگی -->
    <div class="weekly-progress">
        <div class="label"><i class="fas fa-chart-simple"></i> کارهای انجام شده</div>
        <div class="stats">
            <div class="stat-item done"><i class="fas fa-check-circle"></i> <span class="num" id="doneCount">۰</span></div>
            <div class="stat-item undone"><i class="fas fa-circle-minus"></i> <span class="num" id="undoneCount">۰</span></div>
        </div>
    </div>

    <!-- فوتر -->
    <div class="footer">
        <i class="fas fa-paw"></i> ساخته شده برای لپ کیکی من
    </div>

    <!-- نوار وضعیت -->
    <div class="progress-strip">
        <span class="status-label">انجام نشد</span>
        <span style="color:#d45a86;"><i class="fas fa-arrow-left"></i></span>
        <span class="status-label done">انجام شد</span>
        <span style="color:#d45a86;"><i class="fas fa-arrow-right"></i></span>
        <span class="panda-badge">🐼</span>
    </div>
</div>

<!-- مدال پاندا -->
<div class="panda-modal" id="pandaModal">
    <div class="modal-content">
        <img src="https://uploadkon.ir/uploads/392b04_261788166539081.jpg" alt="پاندای کیوت" id="pandaImage">
        <div class="emoji-overlay" id="emojiOverlay"></div>
    </div>
</div>

<script>
    (function() {
        // === داده‌ها: همه چک‌باکس‌ها در حالت false (انجام نشده) ===
        let habits = [
            { name: 'عادت جدید', checks: [false, false, false, false, false, false, false] }
        ];

        const saved = localStorage.getItem('pandaHabits');
        if (saved) {
            try {
                const parsed = JSON.parse(saved);
                if (Array.isArray(parsed) && parsed.length > 0) {
                    // اطمینان از اینکه همه چک‌باکس‌ها false باشند
                    habits = parsed.map(h => ({
                        name: h.name || 'عادت',
                        checks: h.checks ? h.checks.map(() => false) : [false, false, false, false, false, false, false]
                    }));
                }
            } catch(e) {}
        }

        // بازنویسی برای اطمینان: همه false
        habits = habits.map(h => ({
            name: h.name || 'عادت',
            checks: [false, false, false, false, false, false, false]
        }));

        function saveHabits() {
            localStorage.setItem('pandaHabits', JSON.stringify(habits));
        }

        function renderTable() {
            const tbody = document.getElementById('habitsBody');
            tbody.innerHTML = '';
            let totalDone = 0, totalUndone = 0;

            habits.forEach((habit, index) => {
                const tr = document.createElement('tr');

                const tdLabel = document.createElement('td');
                tdLabel.style.textAlign = 'right';
                const labelDiv = document.createElement('div');
                labelDiv.className = 'habit-label-cell';
                const icon = document.createElement('i');
                icon.className = 'fas fa-paw';
                const inputName = document.createElement('input');
                inputName.type = 'text';
                inputName.className = 'habit-text';
                inputName.value = habit.name;
                inputName.placeholder = 'نام عادت...';
                inputName.addEventListener('change', function() {
                    habit.name = this.value.trim() || 'عادت';
                    saveHabits();
                });
                labelDiv.appendChild(icon);
                labelDiv.appendChild(inputName);
                tdLabel.appendChild(labelDiv);
                tr.appendChild(tdLabel);

                for (let i = 0; i < 7; i++) {
                    const td = document.createElement('td');
                    const checkBox = document.createElement('div');
                    checkBox.className = 'check-box' + (habit.checks[i] ? ' filled' : '');
                    const iconCheck = document.createElement('i');
                    iconCheck.className = habit.checks[i] ? 'fas fa-check' : 'fas fa-minus';
                    checkBox.appendChild(iconCheck);
                    checkBox.addEventListener('click', function() {
                        habit.checks[i] = !habit.checks[i];
                        if (habit.checks[i]) {
                            this.classList.add('filled');
                            this.querySelector('i').className = 'fas fa-check';
                        } else {
                            this.classList.remove('filled');
                            this.querySelector('i').className = 'fas fa-minus';
                        }
                        saveHabits();
                        updateProgress();
                    });
                    td.appendChild(checkBox);
                    tr.appendChild(td);
                }

                const tdDel = document.createElement('td');
                const delBtn = document.createElement('button');
                delBtn.className = 'delete-habit';
                delBtn.innerHTML = '<i class="fas fa-trash-can"></i>';
                delBtn.addEventListener('click', function() {
                    habits.splice(index, 1);
                    if (habits.length === 0) {
                        habits.push({ name: 'عادت جدید', checks: [false, false, false, false, false, false, false] });
                    }
                    saveHabits();
                    renderTable();
                    updateProgress();
                });
                tdDel.appendChild(delBtn);
                tr.appendChild(tdDel);

                tbody.appendChild(tr);

                habit.checks.forEach(v => {
                    if (v) totalDone++;
                    else totalUndone++;
                });
            });

            document.getElementById('doneCount').textContent = totalDone;
            document.getElementById('undoneCount').textContent = totalUndone;
        }

        function updateProgress() {
            let done = 0, undone = 0;
            habits.forEach(h => h.checks.forEach(v => v ? done++ : undone++));
            document.getElementById('doneCount').textContent = done;
            document.getElementById('undoneCount').textContent = undone;
        }

        function addNewHabit() {
            const input = document.getElementById('newHabitInput');
            const name = input.value.trim() || 'عادت جدید 🐼';
            habits.push({ name: name, checks: [false, false, false, false, false, false, false] });
            saveHabits();
            renderTable();
            updateProgress();
            input.value = '';
        }

        document.getElementById('addHabitBtn').addEventListener('click', addNewHabit);
        document.getElementById('newHabitInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') addNewHabit();
        });

        const goalInput = document.getElementById('userGoal');
        goalInput.addEventListener('change', function() {
            localStorage.setItem('pandaGoal', this.value);
        });
        const savedGoal = localStorage.getItem('pandaGoal');
        if (savedGoal) goalInput.value = savedGoal;

        // === پاندا مدال ===
        const modal = document.getElementById('pandaModal');
        const trigger = document.getElementById('pandaTrigger');
        const emojiOverlay = document.getElementById('emojiOverlay');
        let modalTimeout = null;

        function showPandaModal() {
            // پاک کردن ایموجی‌های قبلی
            emojiOverlay.innerHTML = '';
            // ایجاد ایموجی‌های فش فشه (تعداد کم)
            const emojis = ['🐼', '🌸', '✨', '💕', '🌈', '⭐', '🦋', '🌺', '🎀', '💖'];
            for (let i = 0; i < 18; i++) {
                const span = document.createElement('span');
                span.textContent = emojis[Math.floor(Math.random() * emojis.length)];
                span.style.left = (5 + Math.random() * 90) + '%';
                span.style.top = (5 + Math.random() * 90) + '%';
                span.style.animationDuration = (1.2 + Math.random() * 1.2) + 's';
                span.style.fontSize = (18 + Math.random() * 28) + 'px';
                span.style.animationDelay = (Math.random() * 0.8) + 's';
                emojiOverlay.appendChild(span);
            }

            modal.classList.add('active');

            if (modalTimeout) clearTimeout(modalTimeout);
            modalTimeout = setTimeout(() => {
                modal.classList.remove('active');
                modalTimeout = null;
            }, 10000);
        }

        trigger.addEventListener('click', showPandaModal);

        // کلیک بیرون برای بستن
        modal.addEventListener('click', function(e) {
            if (e.target === modal) {
                modal.classList.remove('active');
                if (modalTimeout) {
                    clearTimeout(modalTimeout);
                    modalTimeout = null;
                }
            }
        });

        renderTable();
        updateProgress();
    })();
</script>

</body>
</html>
