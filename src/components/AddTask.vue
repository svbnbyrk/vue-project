<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="newsUrl" name="newsUrl" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        name="newsDate"
        v-model="newsDate"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
// import Header from './Header'
// import Tasks from './Tasks'
// import Task from './Task';

export default{
    name: 'AddTask',
    data() {
        return {
            newsUrl: '',
            newsDate: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.text){
                alert('Please add task')
                return
            }

            const newTask = {
                id: Math.floor(Math.random() * 100000),
                newsUrl: this.newsUrl,
                newsDate: this.newsDate,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask)

            this.newsUrl = ''
            this.newsDate = ''
            this.reminder = false

            console.log(newTask)
        }
    },
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
