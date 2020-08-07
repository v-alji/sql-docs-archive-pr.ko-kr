---
title: MSSQLSERVER_2570 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 79137d0f70c05c6aa7b758f7e073d152681a14b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729508"
---
# <a name="mssqlserver_2570"></a><span data-ttu-id="06eaf-102">MSSQLSERVER_2570</span><span class="sxs-lookup"><span data-stu-id="06eaf-102">MSSQLSERVER_2570</span></span>
    
## <a name="details"></a><span data-ttu-id="06eaf-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="06eaf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06eaf-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="06eaf-104">Product Name</span></span>|<span data-ttu-id="06eaf-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="06eaf-105">SQL Server</span></span>|  
|<span data-ttu-id="06eaf-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="06eaf-106">Event ID</span></span>|<span data-ttu-id="06eaf-107">2570</span><span class="sxs-lookup"><span data-stu-id="06eaf-107">2570</span></span>|  
|<span data-ttu-id="06eaf-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="06eaf-108">Event Source</span></span>|<span data-ttu-id="06eaf-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="06eaf-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="06eaf-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="06eaf-110">Component</span></span>|<span data-ttu-id="06eaf-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="06eaf-111">SQLEngine</span></span>|  
|<span data-ttu-id="06eaf-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="06eaf-112">Symbolic Name</span></span>|<span data-ttu-id="06eaf-113">DBCC_COLUMN_VALUE_OUT_OF_RANGE</span><span class="sxs-lookup"><span data-stu-id="06eaf-113">DBCC_COLUMN_VALUE_OUT_OF_RANGE</span></span>|  
|<span data-ttu-id="06eaf-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="06eaf-114">Message Text</span></span>|<span data-ttu-id="06eaf-115">개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)의 페이지 P_ID, 슬롯 S_ID.</span><span class="sxs-lookup"><span data-stu-id="06eaf-115">Page P_ID, slot S_ID in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="06eaf-116">열 COLUMN_NAME 값이 데이터 형식 "DATATYPE"의 범위를 벗어났습니다.</span><span class="sxs-lookup"><span data-stu-id="06eaf-116">Column COLUMN_NAME value is out of range for data type "DATATYPE".</span></span> <span data-ttu-id="06eaf-117">열을 유효한 값으로 업데이트하십시오.</span><span class="sxs-lookup"><span data-stu-id="06eaf-117">Update column to a legal value.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="06eaf-118">설명</span><span class="sxs-lookup"><span data-stu-id="06eaf-118">Explanation</span></span>  
 <span data-ttu-id="06eaf-119">지정한 열에 포함된 열 값이 열 데이터 형식에 대해 가능한 값의 범위를 벗어났습니다.</span><span class="sxs-lookup"><span data-stu-id="06eaf-119">The column value that is contained in the specified column is outside the range of possible values for the column data type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="06eaf-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="06eaf-120">User Action</span></span>  
 <span data-ttu-id="06eaf-121">복구할 수 없는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="06eaf-121">The error is not repairable.</span></span> <span data-ttu-id="06eaf-122">열을 해당 열 데이터 형식 범위 내의 값으로 업데이트하고 명령을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="06eaf-122">Update the column to a value within the range for the data type of the column and run the command again.</span></span>  <span data-ttu-id="06eaf-123">자세한 내용은 기술 자료 문서 [923247](https://support.microsoft.com/kb/923247)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06eaf-123">For more information, see this KB article [923247](https://support.microsoft.com/kb/923247).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06eaf-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06eaf-124">See Also</span></span>  
 <span data-ttu-id="06eaf-125">[UPDATE&#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="06eaf-125">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span></span>  
 [<span data-ttu-id="06eaf-126">데이터 형식&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06eaf-126">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
