This is your daily operational checklist. Every time you restart your Windows laptop, the background Docker engine goes to sleep.

Here is the exact 4-step sequence you need to execute to bring your entire Big Data syllabus environment back online and enter your terminals.

---

### Step 0: Start the Engine

Before typing any commands, **open the Docker Desktop app** from your Windows Start Menu.
*(Wait until the whale icon in your bottom-right taskbar says "Docker Desktop is running").*

### Step 1: Navigate to the Infrastructure Directory

Open your Command Prompt or PowerShell and point it to the folder where your `docker-compose.yml` file is saved.

```cmd
E:
cd E:\BigData

```

### Step 2: Ignite the Cluster

Command the Docker daemon to wake up all 4 databases (Hadoop, Hive, HBase, and Cassandra) in the background.

```cmd
docker compose up -d

```

*(It will say "Started" next to each container. Because you already downloaded the images, this will only take 2 seconds).*

### Step 3: Verify the Heartbeat

Always run a health check before trying to code.

```cmd
docker ps

```

*Look at the `STATUS` column. It should say `Up X seconds` for all four containers.*

---

### Step 4: Enter Your Workspaces (The Entry Codes)

Once the cluster is awake, you can leave that Command Prompt open and use it to jump into whichever syllabus module you need to practice today.

**To practice HDFS File Commands (Unit I & II):**

```cmd
docker exec -it hadoop bash

```

**To practice Hive Data Warehousing (Unit IV):**

```cmd
docker exec -it hive hive

```

**To practice HBase NoSQL (Unit V):**

```cmd
docker exec -it hbase hbase shell

```

**To practice Cassandra CQL (Unit VI):**

```cmd
docker exec -it cassandra cqlsh

```

Which module are you planning to execute your first set of queries on today?
