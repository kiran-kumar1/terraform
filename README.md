resource "aws_iam_user" "arun" {
  name = "arunproject"
  path = "${("/ploicy.json/")}"
}

resource "aws_iam_access_key" "arun" {
  user    = "${aws_iam_user.arun.name}"
  pgp_key = "keybase:some_person_that_exists"
}

output "secret" {
  value = "${aws_iam_access_key.arun.encrypted_secret}"
}
