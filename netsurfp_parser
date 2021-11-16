# Copyright (c) 2021 Christian Balbin
# This work is licensed under the terms of the MIT license.
# For a copy, see <https://opensource.org/licenses/MIT>.

import csv


def NETSURFPparser(path):

    with open(path) as csvfile:
        reader = csv.DictReader(csvfile)

        seq_dict = {}
        for field in reader.fieldnames:
            seq_dict[field] = []

        first_row = next(reader)

        title = first_row["id"]
        for field in reader.fieldnames:
            seq_dict[field] = [first_row[field]]

        for row in reader:
            if row["id"] == title:

                for field in reader.fieldnames:
                    seq_dict[field].append(row[field])

            else:
                yield seq_dict

                for field in reader.fieldnames:
                    seq_dict[field] = [row[field]]

                title = row["id"]
        #
        yield seq_dict


if __name__ == "__main__":
    for x in NETSURFPparser("netsurfp/616DCFBD0000188B0F41494C.csv"):
        print(x["id"], x["rsa"])
        break
