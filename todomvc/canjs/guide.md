--
layout: todomvc
title: CanJS TodoMVC
path: /todomvc/feathers/canjs
description: A real-time TodoMVC example using CanJS and Feathers
--

<section id="todoapp">
</section>
<footer id="info">
  <p>Double-click to edit a todo</p>
  <p>Written by <a href="http://bitovi.com">Bitovi</a></p>
  <p>Part of <a href="http://todomvc.com">TodoMVC</a></p>
</footer>
<script type="text/mustache" id="app-template">
  <todo-app>
    <header id="header">
      <h1>todos</h1>
      <input id="new-todo" placeholder="What needs to be done?" autofocus="" can-enter="createTodo">
    </header>
    <section id="main" class="{{^if todos.length}}hidden{{/if}}">
      <input id="toggle-all" type="checkbox" {{#if todos.allComplete}}checked="checked"{{/if}} can-click="toggleAll">
      <label for="toggle-all">Mark all as complete</label>
      <ul id="todo-list">
        {{#each displayList}}
        <li class="todo{{#if complete}} completed{{/if}}{{#if editing}} editing{{/if}}">
          <div class="view">
            <input class="toggle" type="checkbox" can-value="complete">
            <label can-dblclick="edit">{{text}}</label>
            <button class="destroy" can-click="destroy"></button>
          </div>
          <input class="edit" type="text" value="{{text}}" can-blur="updateTodo"
            can-keyup="cancelEditing" can-enter="updateTodo">
        </li>
        {{/each}}
      </ul>
    </section>

    <footer id="footer" class="{{^if todos.length}}hidden{{/if}}">
      <span id="todo-count">
        <strong>{{todos.remaining}}</strong> {{plural "item" todos.remaining}} left
      </span>
      <ul id="filters">
        <li>{{{link "All" undefined}}}</li>
        <li>{{{link "Active" "active"}}}</li>
        <li>{{{link "Completed" "completed"}}}</li>
      </ul>
      <button id="clear-completed" class="{{^if todos.completed.length}}hidden{{/if}}" can-click="clearCompleted">
        Clear completed
      </button>
    </footer>
  </todo-app>
</script>
<script src="http://todos.feathersjs.com/socket.io/socket.io.js"></script>
<script src="{{page.path}}/node_modules/todomvc-common/base.js"></script>
<script src="{{page.path}}/node_modules/jquery/dist/jquery.js"></script>
<script src="{{page.path}}/node_modules/canjs/can.jquery.js"></script>
<script type="text/javascript" src="{{page.path}}/node_modules/feathers-client/dist/feathers.js"></script>
<script type="text/javascript" src="{{page.path}}/node_modules/canjs-feathers/dist/canjs-feathers.js"></script>
<script src="{{page.path}}/js/models/todo.js"></script>
<script src="{{page.path}}/js/components/todo-app.js"></script>
<script src="{{page.path}}/js/app.js"></script>
