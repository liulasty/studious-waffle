```xml
<select id = "searchTaskAcceptRecord" resultType = "com.lz.pojo.vo.TaskAcceptRecord">  
   select AcceptRecordId as id,r.taskId as taskId, accepterId as acceptorId, str, acceptTime,   t.status as taskStatus, location, description, t.taskType as taskType, r.status as status   from taskacceptrecords r   left join task t on r.taskId = t.TaskID   <where>  
      <if test = "accepterId != null and accepterId != ''">  
         and r.AccepterId = #{accepterId}      </if>  
      <if test = "taskId != null and taskId != ''">  
         and r.taskId = #{taskId}      </if>  
      <if test = "taskStatus != null">  
         and t.STATUS = #{taskStatus}      </if>  
      <if test = "location != null and location != ''">  
         and t.location like concat('%',#{location},'%')      </if>  
      <if test = "description != null and description != ''">  
         and t.description like concat('%',#{description},'%')      </if>  
      <if test = "taskType != null">  
         and t.taskType = #{taskType}      </if>  
   </where>  
   ORDER BY      <if test = "isAsc == 1">  
         acceptTime DESC      </if>  
      <if test = "isAsc == 0">  
         acceptTime ASC      </if>  
</select>
```
