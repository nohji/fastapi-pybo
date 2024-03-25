<script>
    import fastapi from "../lib/api";
    import { link } from 'svelte-spa-router'

    let question_list = []
  
    function get_question_list() {
      fastapi('get', '/api/question/list', {}, (json) => {
        question_list = json
      })
    }
  
    get_question_list()
  </script>
  
  <ul>
    {#each question_list as question}
        <!-- 해시 기반 라우팅 : 서버로 요청이 발생하지 않음 -->
      <li><a use:link href="/detail/{question.id}">{question.subject}</a></li>
    {/each}
  </ul>