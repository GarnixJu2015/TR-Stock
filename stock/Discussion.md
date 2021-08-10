4. What happens in case the websocket disconnects? How would you go further to keep
the live data available or inform the user? Please discuss the challenges.

- if the connection is lost, could try to reconnect the socket every 10 secs using error/retry function 
```javascript=
retryWhen((errors) => errors.pipe(delay(this.RETRY_SECONDS)))
```


5. What happens if a user adds an instrument multiple times to his list? 

- UI
    - The origin list used the  selection list which allowed multiple choices.
- Data process
    - Build an extra dictionary **mappingDic** with the inic as key, all four fileds in the form of **StockMessage[]** as values.
     - When register a new stock and get a new msg, insert/replace msg according to its inic key
    - Variable **datasource** will be the items of **mappingDic**
