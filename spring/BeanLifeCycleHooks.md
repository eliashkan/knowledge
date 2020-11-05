# Lifecycle Hooks for Spring Beans

Implementing the interfaces InitializingBean, DisposableBean, BeanNameAware will work with core, but the @PostConstruct and @PreDestroy annotations will only work with Spring Boot or the JSR-250 API. 

```xml
<dependency>
	<groupId>javax.annotation</groupId>
	<artifactId>jsr250-api</artifactId>
	<version>1.0</version>
</dependency>
```

```java
    @Component
public class LifeCycleDemoBean implements InitializingBean, DisposableBean, BeanNameAware,
        BeanFactoryAware, ApplicationContextAware {​​​​​​
    public LifeCycleDemoBean() {​​​​​​
        System.out.println("## I'm in the LifeCycleBean Constructor");
    }​​​​​​
    @Override
    public void destroy() throws Exception {​​​​​​
        System.out.println("## The Lifecycle bean has been terminated");
    }​​​​​​
    @Override
    public void afterPropertiesSet() throws Exception {​​​​​​
        System.out.println("## The LifeCycleBean has its properties set!");
    }​​​​​​
    @Override
    public void setBeanFactory(BeanFactory beanFactory) throws BeansException {​​​​​​
        System.out.println("## Bean Factory has been set");
    }​​​​​​
    @Override
    public void setBeanName(String name) {​​​​​​
        System.out.println("## My Bean Name is: " + name);
    }​​​​​​
    @Override
    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {​​​​​​
        System.out.println("## Application context has been set");
    }​​​​​​
    @PostConstruct
    public void postConstruct(){​​​​​​
        System.out.println("## The Post Construct annotated method has been called");
    }​​​​​​
    @PreDestroy
    public void preDestroy() {​​​​​​
        System.out.println("## The Predestroy annotated method has been called");
    }​​​​​​
    public void beforeInit(){​​​​​​
        System.out.println("## - Before Init - Called by Bean Post Processor");
    }​​​​​​
    public void afterInit(){​​​​​​
        System.out.println("## - After init called by Bean Post Processor");
    }​​​​​​
}​​​​​​
```