---
title: 변경 캡처를 위해 선택된 테이블 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 258eb8e761ac697bebd630cc0e627941b4ffc7d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648510"
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a><span data-ttu-id="9c92c-102">변경 캡처를 위해 선택된 테이블 변경</span><span class="sxs-lookup"><span data-stu-id="9c92c-102">Make Changes to the Tables Selected for Capturing Changes</span></span>
  <span data-ttu-id="9c92c-103">이 대화 상자에서 변경을 캡처할 선택된 테이블의 특정 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-103">In this dialog box, you can select specific columns from the selected table to capture changes from.</span></span> <span data-ttu-id="9c92c-104">또한 **보안 역할** 및 **캡처 인스턴스** 정보를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-104">You can also edit the **Security Role** and **Capture Instance** information.</span></span>  
  
 <span data-ttu-id="9c92c-105">이 대화 상자에서 변경을 캡처하도록 선택한 테이블을 다음과 같이 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-105">You can make the following changes to the tables you selected for capturing changes in this dialog box.</span></span>  
  
 <span data-ttu-id="9c92c-106">**CDC 인스턴스에 포함되는 열 변경:**</span><span class="sxs-lookup"><span data-stu-id="9c92c-106">**Make changes to which columns are included in the CDC instance:**</span></span>  
  
 <span data-ttu-id="9c92c-107">다음 중 하나 또는 모두를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-107">Do one or both of the following:</span></span>  
  
-   <span data-ttu-id="9c92c-108">포함할 추가 열의 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-108">Select the check box next to any additional column you want to include.</span></span>  
  
-   <span data-ttu-id="9c92c-109">더 이상 포함하지 않을 열의 옆에 있는 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-109">Clear the check box next to any column that you no longer want to include.</span></span>  
  
 <span data-ttu-id="9c92c-110">**특정 열의 데이터 형식 변경**:</span><span class="sxs-lookup"><span data-stu-id="9c92c-110">**Change the data type for a specific column**:</span></span>  
  
 <span data-ttu-id="9c92c-111">특정 열에 대해 다른 데이터 형식을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-111">You can select a different data type for a specific column.</span></span> <span data-ttu-id="9c92c-112">원본 데이터 형식과 호환되는 데이터 형식으로만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-112">You can only change the data type to a data type that is compatible with the original data type.</span></span>  
  
 <span data-ttu-id="9c92c-113">데이터 형식을 변경하려면 **데이터 형식** 열을 클릭하고 다른 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-113">To change the data type, click in the **Data Type** column and select a different data type.</span></span> <span data-ttu-id="9c92c-114">원본 데이터 형식과 호환되는 데이터 형식만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-114">Only data types that are compatible with the original data type are available.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c92c-115">추가 데이터 형식을 선택할 수 없는 경우 드롭다운 목록이 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-115">If no additional data types can be selected, the drop-down list is not available.</span></span>  
  
 <span data-ttu-id="9c92c-116">**보안 역할 변경**</span><span class="sxs-lookup"><span data-stu-id="9c92c-116">**Change the Security Role**</span></span>  
  
 <span data-ttu-id="9c92c-117">**보안 역할** 필드에서 새 이름을 입력하거나 보안 제어 역할의 이름을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-117">Type a new name or edit the name of the security gating role in the **Security Role** field.</span></span>  
  
 <span data-ttu-id="9c92c-118">**캡처 인스턴스 변경 또는 추가**</span><span class="sxs-lookup"><span data-stu-id="9c92c-118">**Change or add a capture instance**</span></span>  
  
 <span data-ttu-id="9c92c-119">**캡처 인스턴스** 필드에 캡처 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9c92c-119">In the **Capture Instance** field enter a name for the capture instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c92c-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c92c-120">See Also</span></span>  
 <span data-ttu-id="9c92c-121">[SQL Server 변경 데이터베이스 인스턴스를 만드는 방법](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="9c92c-121">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="9c92c-122">Oracle 테이블 및 열 선택</span><span class="sxs-lookup"><span data-stu-id="9c92c-122">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
