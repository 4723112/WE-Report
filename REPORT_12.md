# 第12回 Webエンジニアリング演習 レポート
## 学籍番号（名前は書かなくてよい）
4723112
## 本日の感想
講義に参加することが出来ず、わからないことが多く難しかった。
まだ本時の発展を行うので、しっかり復習したいと思う。
## 実装したコード
App.Vue
<script setup lang="ts">
  import { ref, computed } from 'vue';
  // 1. AddTodoコンポーネントをインポート
  import AddTodo from './components/AddTodo.vue';
  
  type Todo = { id: number; title: string; completed: boolean };
  
  const todos = ref<Todo[]>([
    { id: 1, title: 'Buy groceries', completed: false },
    { id: 2, title: 'Write report', completed: true },
    { id: 3, title: 'Call Alice', completed: false },
  ]);
  
  const kensuu = computed(() => {
    return todos.value.filter(todo => !todo.completed).length;
  });
  
  const newTitle = ref('');
  const nextId = ref(Math.max(0, ...todos.value.map((t) => t.id)) + 1);
  
  function addTodo() {
    if (!newTitle.value) return;
    todos.value.push({ id: nextId.value++, title: newTitle.value, completed: false });
    newTitle.value = ''; // defineModelにより子側のinputも空になります
  }
  </script>
  
  <template>
    <div id="app">
      <section class="todo-app">
        <h2>Todos</h2>
        <p>未完了のタスク数: {{kensuu}}</p>
        <ul>
          <li
            v-for="todo in todos"
            :key="todo.id"
            style="display:flex; align-items:center; gap:0.5rem; margin:0.25rem 0;"
          >
            <input type="checkbox" v-model="todo.completed" />
            <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
              {{ todo.title }}
            </span>
          </li>
        </ul>
      </section>
  
      <AddTodo 
        v-model:message="newTitle" 
        @add-todo="addTodo" 
      />
    </div>
  </template>

  AddTodo.vue
  <script setup>
    // 親から v-model:message で渡されたデータと同期する
    const model = defineModel("message")
    
    // 追加ボタンが押されたことを親に知らせるためのイベントを定義
    const emit = defineEmits(['add-todo'])
    
    function handleAdd() {
        // 親コンポーネントの addTodo 関数を発火させるための通知
        emit('add-todo')
    }
    </script>
    
    <template>
      <section>
        <h2>New Todo</h2>
        <div style="display: flex; align-items: center; gap: 0.5rem; margin: 0.25rem 0;">
          <input
            v-model="model"
            placeholder="New todo title"
            aria-label="New todo title"
          />
          <button v-on:click="handleAdd" :disabled="!model">Add</button>
        </div>
      </section>
    </template>