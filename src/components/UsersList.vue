<template>
  <div>
    <slot>
      UsersList
    </slot>
    <div v-for="user in users" :key="user.id">
      <UserListItem
        class="UserList_Item"
        :id="user.id"
        :firstName="user.firstName"
        :lastName="user.lastName"
        :gender="user.gender"
        @select="onSelect"
        @remove="onRemove"
      />
    </div>
    <slot name="footer"></slot>
  </div>
</template>

<script>
import UserListItem from './UserListItem.vue'
export default {
  name: 'UsersList',
  props: {
    users: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    onSelect({id}) {
      this.$emit('select', {id})
    },
    onRemove({id}) {
      this.$emit('remove', {id})
    },
  },
  components: {
    UserListItem,
  },
}
</script>
