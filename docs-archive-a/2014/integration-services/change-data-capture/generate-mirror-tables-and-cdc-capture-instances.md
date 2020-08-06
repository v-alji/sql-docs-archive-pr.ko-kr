---
title: 미러 테이블 및 CDC 캡처 인스턴스 생성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78daea310112cf7e9e78e489097fe9a76e69996b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728623"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a><span data-ttu-id="a89b3-102">미러 테이블 및 CDC 캡처 인스턴스 생성</span><span class="sxs-lookup"><span data-stu-id="a89b3-102">Generate Mirror Tables and CDC Capture Instances</span></span>
  <span data-ttu-id="a89b3-103">미러 테이블 생성 페이지를 사용하여 CDC 인스턴스에 포함된 테이블에 대한 미러 테이블 생성</span><span class="sxs-lookup"><span data-stu-id="a89b3-103">Use the Generate Mirror Tables page to generate the mirror tables for the tables you included in the CDC instance</span></span>  
  
 <span data-ttu-id="a89b3-104">**실행** 을 클릭하여 미러 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a89b3-104">Click **Run** to create the mirror tables.</span></span> <span data-ttu-id="a89b3-105">각 테이블 만들기의 진행률이 표시되고 각 미러 테이블이 성공적으로 완료되었는지 오류가 발생했는지 알려주는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89b3-105">The progress for the creation of each table is displayed and a message is displayed to let you know whether each mirror table is completed successfully or with errors.</span></span> <span data-ttu-id="a89b3-106">오류가 발생한 경우 **자세히** 를 클릭하면 오류에 대한 설명이 표시된 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a89b3-106">If any errors occur, click **Details** to see a dialog box with an explanation of the error.</span></span>  
  
 <span data-ttu-id="a89b3-107">테이블을 만들지 못한 경우 계속하기 전에 실패한 테이블을 삭제하거나 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a89b3-107">If any of the tables fail to be created, you can choose to continue or delete any tables that failed before continuing.</span></span> <span data-ttu-id="a89b3-108">마법사를 완료한 후 Oracle 원본 데이터베이스에서 테이블을 수정할지 CDC 인스턴스에서 테이블을 사용하지 않을지 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a89b3-108">After you finish running the wizard, you can decide whether to fix the table in the Oracle source database or not use it in the CDC instance.</span></span> <span data-ttu-id="a89b3-109">테이블을 수정하는 경우 [Edit Tables](edit-tables.md)시 테이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a89b3-109">If you fix the table, you can add it when you [Edit Tables](edit-tables.md).</span></span>  
  
 <span data-ttu-id="a89b3-110">**다음** 을 클릭하여 [Finish](finish.md) 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a89b3-110">Click **Next** to open the [Finish](finish.md) page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89b3-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a89b3-111">See Also</span></span>  
 [<span data-ttu-id="a89b3-112">SQL Server 변경 데이터베이스 인스턴스를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="a89b3-112">How to Create the SQL Server Change Database Instance</span></span>](how-to-create-the-sql-server-change-database-instance.md)  
  
  
