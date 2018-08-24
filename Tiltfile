
def millie():
  return composite_service([milliefe, vigoda, fortune])

def milliefe():
  yaml = local_file('milliefe.yaml')
  img = build_docker_image('Dockerfile.base', 'windmill.build/millie/milliefe', '/go/bin/milliefe')
  repo = local_git_repo('../milliefe')
  img.add('/go/src/github.com/dbentley/milliefe', repo)
  img.run('time go install github.com/dbentley/milliefe')
  return k8s_service(yaml, img)

def vigoda():
  yaml = local_file('vigoda.yaml')
  img = build_docker_image('Dockerfile.base', 'windmill.build/millie/vigoda', '/go/bin/vigoda')
  repo = local_git_repo('../vigoda')
  img.add('/go/src/github.com/dbentley/vigoda', repo)
  img.run('time go install github.com/dbentley/vigoda')
  return k8s_service(yaml, img)

def fortune():
  yaml = local_file('fortune.yaml')
  img = build_docker_image('Dockerfile.base', 'windmill.build/millie/fortune', '/go/bin/fortune')
  repo = local_git_repo('../fortune')
  img.add('/go/src/github.com/dbentley/fortune', repo)
  img.run('cd /go/src/github.com/dbentley/fortune && time make install')
  return k8s_service(yaml, img)

def local_file(p):
  return local("cat %s" % p)
