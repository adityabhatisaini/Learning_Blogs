Steps
1. We have to use power atomate.

// DAX Query
DEFINE
	VAR __DS0Core = 
		SUMMARIZE(
			'NewTable',
			'NewTable'[Employee Code],
			'NewTable'[Employee Name],
			'NewTable'[Level 1],
			'NewTable'[Level 2],
			'NewTable'[Level 3],
			'NewTable'[Level 4],
			'NewTable'[Level 5],
			'NewTable'[Level 6],
			'NewTable'[Level 7],
			'NewTable'[Level 8]
		)

	VAR __DS0PrimaryWindowed = 
		TOPN(
			501,
			__DS0Core,
			'NewTable'[Level 7],
			0,
			'NewTable'[Employee Code],
			1,
			'NewTable'[Employee Name],
			1,
			'NewTable'[Level 1],
			1,
			'NewTable'[Level 2],
			1,
			'NewTable'[Level 3],
			1,
			'NewTable'[Level 4],
			1,
			'NewTable'[Level 5],
			1,
			'NewTable'[Level 6],
			1,
			'NewTable'[Level 8],
			1
		)

EVALUATE
	__DS0PrimaryWindowed

ORDER BY
	'NewTable'[Level 7] DESC,
	'NewTable'[Employee Code],
	'NewTable'[Employee Name],
	'NewTable'[Level 1],
	'NewTable'[Level 2],
	'NewTable'[Level 3],
	'NewTable'[Level 4],
	'NewTable'[Level 5],
	'NewTable'[Level 6],
	'NewTable'[Level 8]
