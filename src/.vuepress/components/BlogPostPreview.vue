<script>
export default {
  name: "BlogPostPreview",
  props: {
    publishDate: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    path: {
      type: String,
      required: true
    },
    excerpt: {
      type: String,
      required: false
    }
  },
  computed: {
    formatPublishDate() {
      const dateFormat = new Date(this._props.publishDate);
      const options = {
        year: "numeric",
        month: "long",
        day: "numeric"
      };

      return dateFormat.toLocaleDateString("en-US", options);
    }
  }
};
</script>

<template>
  <section class="blog-post">
    <time class="publish-date">{{ formatPublishDate }}</time>
    <h3 class="blog-post__title"><a :href="path">{{ title }}</a></h3>
    <p v-if="excerpt">{{ excerpt }}</p>
    <a
      class="read-more"
      :href="path"
    >Read More</a>
  </section>
</template>

<style lang="stylus">
.blog-post {
  padding: 20px 0 0 0;
  margin: 20px 0 0 0;
  border-top: 1px solid #dad6d6;
}

.blog-post__button {
  margin-bottom: 1.5rem;
  display: inline-block;
}

.blog-post__title {
  font-size: 22px;
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
}

.blog-post__title a {
  border: 0;
  color: $textColor;
  font-weight: 600;
}

.blog-post__title a:hover {
  color: #7e00de;
  text-decoration: none !important;
}

.publish-date {
  font-size: 13px;
  text-transform: uppercase;
}

p {
  margin: 0 0 25px;
}

.read-more {
  font-size: 14px;
  font-weight: 600;
  transition: all 0.2s ease-in-out;
  text-decoration: none !important;
  display: inline-block;
  border-bottom: 1px solid transparent;
}

.read-more:hover {
  border-color: #7e00de;
}

.tag-list {
  list-style: none;
  padding-left: 0;
  display: flex;
  margin-bottom: 25px;
}

.tag-list__item {
  margin-left: 10px;
}

.tag-list__item:first-child {
  margin-left: 0;
}

.tag-list__btn {
  padding: 5px;
  font-size: 0.9rem;
  background-color: #fff;
}
</style>
