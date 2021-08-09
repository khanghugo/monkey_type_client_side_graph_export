// getting some info
var chunk;
let test_completed_raw = document.getElementsByClassName(
    "group globalTestsCompleted").item(
        0).innerText;
let test_completed_regex = /([0-9])\d+/;
var test_completed_num = Number(test_completed_raw.match(test_completed_regex)[0]);

// loading pages
var load_count = Math.ceil((test_completed_num) / 10); // as of now, each "load more" gives 10 more entries
for (let i = 0; i < load_count + 1; i++) {
    try {
        $(".pageAccount .loadMoreButton").click();
        }
    catch (e) {}
    }

// formatting
// trimming
let text = document.getElementsByClassName("group history").item(0).innerText.trim();
// spae to none
let space_regex = /\s{2,}/;
chunk = text.split(space_regex);
// splitting tab
for (let i in chunk) {
	// console.log(i);
	chunk[i] = chunk[i].split("\t");
    // merging lonely standing dates
	if (chunk[i].length == 1) {
		chunk[i][0] = chunk[i][0].replace("\n", " ") + "\n";
		chunk[i-1].push(chunk[i][0]);
	}
}
// removing half of the chunk because i am not using a clean implementation
for (let i in chunk) {
	if (chunk[i].length == 1) {
		chunk.splice(i, 1);
	}
}
// removing mode, info, and tag
const remove_list = ["info", "tags"];
for (var i in remove_list) {
	chunk[0].splice(chunk[0].indexOf(remove_list[i]), 1)
}
// \n to space
chunk[0][3] = chunk[0][3].replace("\n", " ");
chunk[0][4] = chunk[0][4].replace("\n", " ");
// add \n to [0]
chunk[0][chunk[0].length - 1] += "\n"

// Blob / source: https://jsfiddle.net/mdearman/d1zpndcu/
if (window.Blob == undefined || window.URL == undefined || window.URL.createObjectURL == undefined) {
  alert("Your browser doesn't support Blobs");
}
var csvFile;
var downloadLink;
var filename = "MK.csv";
csvFile = new Blob(chunk, {
    type: "text/csv"
  });
downloadLink = document.createElement("a");
  downloadLink.download = filename;
  downloadLink.href = window.URL.createObjectURL(csvFile);
  downloadLink.style.display = "none";
  document.body.appendChild(downloadLink);
  downloadLink.click();
