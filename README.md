# audibene_recruitment
- Created by Andrzej Brozyniak brozyniakandrzej@gmail.com
# Assumption
   * ##Jenkins  
    * Jenkins 2.x  
    * Installed plugins :
        * JavaScript GUI Lib: Handlebars bundle plugin (handlebars): 1.1.1
        *Pipeline: Declarative Extension Points API (pipeline-model-extensions): 1.7.2
        * JavaScript GUI Lib: Handlebars bundle plugin (handlebars): 1.1.1
        * Pipeline: Declarative Extension Points API (pipeline-model-extensions): 1.7.2
        * Plain Credentials Plugin (plain-credentials): 1.7
        * Pipeline: Stage View Plugin (pipeline-stage-view): 2.15
        * Branch API Plugin (branch-api): 2.6.0
        * GitHub API Plugin (github-api): 1.116
        * JavaScript GUI Lib: ACE Editor bundle plugin (ace-editor): 1.1
        * Pipeline: Model API (pipeline-model-api): 1.7.2
        * Oracle Java SE Development Kit Installer Plugin (jdk-tool): 1.4
        * Lockable Resources plugin (lockable-resources): 2.8
        * Git plugin (git): 4.4.2
        * Pipeline: Groovy (workflow-cps): 2.83
        * Matrix Authorization Strategy Plugin (matrix-auth): 2.6.3
        * ECharts API Plugin (echarts-api): 4.8.0-2
        * Pipeline: Stage Tags Metadata (pipeline-stage-tags-metadata): 1.7.2
        * Pipeline: GitHub Groovy Libraries (pipeline-github-lib): 1.0
        * GitHub Branch Source Plugin (github-branch-source): 2.9.0
        * Token Macro Plugin (token-macro): 2.12
        * Workspace Cleanup Plugin (ws-cleanup): 0.38
        * Apache HttpComponents Client 4.x API Plugin (apache-httpcomponents-client-4-api): 4.5.10-2.0
        * Docker Commons Plugin (docker-commons): 1.17
        * Timestamper (timestamper): 1.11.5
        * Pipeline: Declarative (pipeline-model-definition): 1.7.2
        * Resource Disposer Plugin (resource-disposer): 0.14
        * Pipeline: Job (workflow-job): 2.40
        * Pipeline: Multibranch (workflow-multibranch): 2.22
        * Plugin Utilities API Plugin (plugin-util-api): 1.2.5
        * Pipeline: Shared Groovy Libraries (workflow-cps-global-lib): 2.17
        * Pipeline: Supporting APIs (workflow-support): 3.5
        * Pipeline: Input Step (pipeline-input-step): 2.12
        * JavaScript GUI Lib: jQuery bundles (jQuery and jQuery UI) plugin (jquery-detached): 1.2.1
        * OkHttp Plugin (okhttp-api): 3.14.9
        * Pipeline: REST API Plugin (pipeline-rest-api): 2.15
        * LDAP Plugin (ldap): 1.26
        * Pipeline: SCM Step (workflow-scm-step): 2.11
        * JUnit Plugin (junit): 1.34
        * Pipeline: Basic Steps (workflow-basic-steps): 2.21
        * GIT server Plugin (git-server): 1.9
        * Display URL API (display-url-api): 2.3.3
        * SSH Build Agents plugin (ssh-slaves): 1.31.2
        * Jackson 2 API Plugin (jackson2-api): 2.11.2
        * GitHub plugin (github): 1.31.0
        * Gradle Plugin (gradle): 1.36
        * Structs Plugin (structs): 1.20
        * Git client plugin (git-client): 3.4.2
        * JQuery3 API Plugin (jquery3-api): 3.5.1-1
        * SSH Credentials Plugin (ssh-credentials): 1.18.1
        * Authentication Tokens API Plugin (authentication-tokens): 1.4
        * Snakeyaml API Plugin (snakeyaml-api): 1.27.0
        * Pipeline: Nodes and Processes (workflow-durable-task-step): 2.36
        * JSch dependency plugin (jsch): 0.1.55.2
        * Pipeline Graph Analysis Plugin (pipeline-graph-analysis): 1.10
        * Command Agent Launcher Plugin (command-launcher): 1.4
        * bouncycastle API Plugin (bouncycastle-api): 2.18
        * SCM API Plugin (scm-api): 2.6.3
        * Pipeline: Milestone Step (pipeline-milestone-step): 1.3.1
        * Folders Plugin (cloudbees-folder): 6.14
        * Matrix Project Plugin (matrix-project): 1.17
        * Mailer Plugin (mailer): 1.32.1
        * Build Timeout (build-timeout): 1.20
        * Pipeline: Step API (workflow-step-api): 2.22
        * Trilead API Plugin (trilead-api): 1.0.10
        * JavaScript GUI Lib: Moment.js bundle plugin (momentjs): 1.1.1
        * Credentials Binding Plugin (credentials-binding): 1.23
        * Pipeline: API (workflow-api): 2.40
        * Pipeline (workflow-aggregator): 2.6
        * Pipeline: Build Step (pipeline-build-step): 2.13
        * Durable Task Plugin (durable-task): 1.35
        * Email Extension Plugin (email-ext): 2.76
        * Pipeline: Stage Step (pipeline-stage-step): 2.5
        * CloudBees Docker Build and Publish plugin (docker-build-publish): 1.3.2
        * OWASP Markup Formatter Plugin (antisamy-markup-formatter): 2.1
        * Script Security Plugin (script-security): 1.74
        * Ant Plugin (ant): 1.11
        * PAM Authentication plugin (pam-auth): 1.6
        * Credentials Plugin (credentials): 2.3.13
        * Docker API Plugin (docker-java-api): 3.1.5.2
        * Docker plugin (docker-plugin): 1.2.0
        * Docker Pipeline (docker-workflow): 1.24
    
   * ##App
    * Simple java application with deployment.yml and service.yml (Load balancer)
    
   * ##Job
    * Multibranch pieline job  
    ** Configured Branch source as GiTHub with discover all branches and discover pull requests from forks and origin,  
       exceptions: do not trigger feature branches automatically (Still it is possible manually)
    ** Discard old items (more than 10)
   * ##Pipeline  
    * Declarative pipeline  
   * ##Github repo
    * Configured webhook for jenkins
    * Configured policy, not possible to commit/merge to develop branch without pull request and only possible merge  
      from develop to master with pull request
    
    
    
