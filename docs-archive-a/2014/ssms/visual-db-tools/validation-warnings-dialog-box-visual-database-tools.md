---
title: 유효성 검사 경고 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65556
- vdt.dlgbox.validationwarnings
ms.assetid: fc76e234-ec9c-4a19-a65b-cb558ec8268e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4f94c3ae91e077af853db949847bc8448f6a4753
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651960"
---
# <a name="validation-warnings-dialog-box-visual-database-tools"></a><span data-ttu-id="8f5f2-102">유효성 검사 경고 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8f5f2-102">Validation Warnings Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="8f5f2-103">이 대화 상자는 잠재적인 손상의 위험이 있는 수정 내용을 저장하려는 경우나 데이터베이스 커밋 작업이 실패할 가능성이 있는 경우에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-103">This dialog box appears if you attempt to save modifications with potentially damaging side effects, or if the database commit operation is likely to fail.</span></span> <span data-ttu-id="8f5f2-104">이 대화 상자에는 위험 요소가 잠재된 사항이 무엇인지 또는 커밋 작업이 실패하는 이유가 무엇인지에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-104">This dialog box indicates what those side effects might be or why the commit operation might fail.</span></span> <span data-ttu-id="8f5f2-105">이러한 정보를 확인하고 그 결과에 따라 수정 작업을 계속 진행하거나 작업을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-105">It gives you the chance to continue with the modification or cancel the operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8f5f2-106">이 대화 상자는 수정 사항을 데이터베이스에 전송하려는 경우나 변경 스크립트를 저장하려는 경우에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-106">This dialog box appears when you attempt to transmit your modifications to the database or when you save a change script.</span></span>  
  
 <span data-ttu-id="8f5f2-107">이 대화 상자는 다음과 같은 이유로 인해 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-107">The dialog box can appear for any of these reasons:</span></span>  
  
-   <span data-ttu-id="8f5f2-108">모든 수정 사항을 커밋하는 데 필요한 데이터베이스 권한이 사용자에게 없는 경우</span><span class="sxs-lookup"><span data-stu-id="8f5f2-108">You might not have database permissions to commit all the modifications.</span></span>  
  
-   <span data-ttu-id="8f5f2-109">해당 사항을 수정하면 잘못된 형식의 파생 열, 기본 제약 조건 또는 CHECK 제약 조건이 발생할 수 있는 경우</span><span class="sxs-lookup"><span data-stu-id="8f5f2-109">Your modifications would result in improperly formed derived columns, default constraints, or check constraints.</span></span>  
  
-   <span data-ttu-id="8f5f2-110">열의 데이터 형식을 수정하여 데이터가 손실될 수 있는 경우</span><span class="sxs-lookup"><span data-stu-id="8f5f2-110">A modification to a column's data type might cause data loss.</span></span>  
  
-   <span data-ttu-id="8f5f2-111">수정 결과로 900바이트보다 큰 인덱스가 생성되는 경우</span><span class="sxs-lookup"><span data-stu-id="8f5f2-111">A modification would result in an index greater than 900 bytes.</span></span>  
  
-   <span data-ttu-id="8f5f2-112">스키마 바인딩된 뷰나 사용자 정의 함수에 관련된 테이블 또는 열이 수정 결과로 인해 변경되는 경우</span><span class="sxs-lookup"><span data-stu-id="8f5f2-112">A modification would change a table or column contributing to a schema-bound view or user-defined function.</span></span>  
  
-   <span data-ttu-id="8f5f2-113">하나 이상의 암호화된 트리거가 있는 테이블이 수정 결과로 인해 재작성되고 트리거가 삭제되는 경우</span><span class="sxs-lookup"><span data-stu-id="8f5f2-113">A modification would result in the re-creation of a table that has one or more encrypted triggers; the triggers will be dropped.</span></span>  
  
-   <span data-ttu-id="8f5f2-114">수정 결과로 인해 한 테이블 내의 열에 대해 ANSI_NULLS나 ANSI_PADDING 또는 이 둘 모두에 대해 중요한 사항이 설정되는 경우</span><span class="sxs-lookup"><span data-stu-id="8f5f2-114">Your modifications will yield noteworthy settings of ANSI_NULLS or ANSI_PADDING or both for the columns within one table.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8f5f2-115">옵션</span><span class="sxs-lookup"><span data-stu-id="8f5f2-115">Options</span></span>  
 <span data-ttu-id="8f5f2-116">**예**</span><span class="sxs-lookup"><span data-stu-id="8f5f2-116">**Yes**</span></span>  
 <span data-ttu-id="8f5f2-117">작업을 계속하여 변경 스크립트를 만들거나 수정 사항을 데이터베이스에 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-117">Proceed with the operation and generate the change script or transmit the modifications to the database.</span></span> <span data-ttu-id="8f5f2-118">데이터베이스를 수정하는 데 필요한 권한이 없거나, 수정 결과로 인해 900바이트보다 큰 인덱스가 생성되거나, 수정 결과로 인해 잘못된 형식의 계산 열, DEFAULT 제약 조건 또는 CHECK 제약 조건이 발생하는 경우에는 커밋 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-118">The commit operation can still fail if you do not have privileges to modify the database, if your modifications will result in an index greater than 900 bytes, or if your modifications will result in an improperly formed computed column, default constraint, or check constraint.</span></span>  
  
 <span data-ttu-id="8f5f2-119">**아니요**</span><span class="sxs-lookup"><span data-stu-id="8f5f2-119">**No**</span></span>  
 <span data-ttu-id="8f5f2-120">저장 동작을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-120">Cancel the save action.</span></span>  
  
 <span data-ttu-id="8f5f2-121">**텍스트 파일 저장**</span><span class="sxs-lookup"><span data-stu-id="8f5f2-121">**Save Text File**</span></span>  
 <span data-ttu-id="8f5f2-122">**다른 이름으로 저장** 대화 상자가 표시됩니다. 이 대화 상자를 사용하면 경고 목록이 포함된 텍스트 파일의 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f5f2-122">Display the **Save As** dialog box, where you can specify a location for a text file containing a list of the warnings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5f2-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f5f2-123">See Also</span></span>  
 <span data-ttu-id="8f5f2-124">[Visual Database Tools를 &#40;테이블 디자인&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8f5f2-124">[Design Tables &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="8f5f2-125">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="8f5f2-125">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
