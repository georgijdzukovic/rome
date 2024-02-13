# ROME
ok

### System Requirements
Starting with ROME 2.x Java 8 or higher is required. The only exception is version 2.0.0, which requires Java 11. However, this has been corrected in version 
2.1.0.

### Dependency (Maven)
```xml
<dependencies>
    <dependency>
        <groupId>com.rometools</groupId>
        <artifactId>rome</artifactId>
        <version>${rome.version}</version>
    </dependency>
</dependencies>
```

### Parse a feed
```java
String url = "https://stackoverflow.com/feeds/tag?tagnames=rome";
SyndFeed feed = new SyndFeedInput().build(new XmlReader(new URL(url)));

System.out.println(feed.getTitle());
```
**Beware!** The `URL` variant used in this example is deprecated and works only for simplest cases. Please consider using a separate library for fetching the 
feed (see examples in [#276](https://github.com/rometools/rome/issues/276)).

### Generate a feed
```java
SyndFeed feed = new SyndFeedImpl();
feed.setFeedType("rss_2.0");
feed.setTitle("test-title");
feed.setDescription("test-description");
feed.setLink("https://example.org");

System.out.println(new SyndFeedOutput().outputString(feed));
```
