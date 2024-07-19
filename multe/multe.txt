# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Multiple Treatment Effects for Contamination Bias Diagnostics Use multe With (In) R Software
install.packages("remotes")
remotes::install_github("kolesarm/multe")
install.packages("readstata13")
install.packages("usethis")
library("multe")
library("readstata13")
library("usethis")
multe <- readstata13::read.dta13("https://raw.githubusercontent.com/timbulwidodostp/multe_r/main/multe/multe.dta", generate.factors=TRUE)
attr(multe, "expansion.fields") <- NULL
attr(multe, "formats") <- NULL
attr(multe, "datalabel") <- NULL
attr(multe, "types") <- NULL
attr(multe, "val.labels") <- NULL
attr(multe, "label.table") <- NULL
attr(multe, "orig.dim") <- NULL
for (j in seq_len(ncol(multe))) {
    if (identical(sort(unique(multe[, j])), c(0L, 1L)))
        multe[, j] <- as.logical(multe[, j])
}
usethis::use_data(multe, overwrite=TRUE, internal=FALSE)
# Estimation Multiple Treatment Effects for Contamination Bias Diagnostics Use multe With (In) R Software
multe <- stats::lm(std_iq_24~race+factor(age_24)+female+SES_quintile, weight=W2C0, data=multe)
summary(multe)
multe <- multe(multe, "race", cluster=NULL)
print(multe, digits=3)
# Multiple Treatment Effects for Contamination Bias Diagnostics Use multe With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished