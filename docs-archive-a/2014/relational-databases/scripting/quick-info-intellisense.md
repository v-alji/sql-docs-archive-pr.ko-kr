---
title: 요약 정보(IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f173c57438301702a8e51acf4531c655fde0cc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743196"
---
# <a name="quick-info-intellisense"></a><span data-ttu-id="4d913-102">요약 정보(IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="4d913-102">Quick Info (IntelliSense)</span></span>
  <span data-ttu-id="4d913-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **요약 정보** 옵션은 코드의 모든 식별자에 대한 완전한 선언을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4d913-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Quick Info** option displays the complete declaration for any identifier in your code.</span></span> <span data-ttu-id="4d913-104">마우스 포인터를 식별자 위로 이동하면 노란색 팝업 창에 해당 선언이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d913-104">When you move the mouse pointer over an identifier, its declaration is displayed in a yellow pop-up window.</span></span> <span data-ttu-id="4d913-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **요약 정보** 는 데이터베이스 엔진 및 XML 쿼리 편집기에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d913-105">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Quick Info** is available in the Database Engine and XML Query Editors.</span></span>  
  
## <a name="transact-sql-quick-info"></a><span data-ttu-id="4d913-106">Transact-SQL 요약 정보</span><span class="sxs-lookup"><span data-stu-id="4d913-106">Transact-SQL Quick Info</span></span>  
 <span data-ttu-id="4d913-107">**쿼리 편집기의** 요약 정보 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에는 두 가지 유형의 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d913-107">**Quick Info** displays two types of information in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="4d913-108">디버그 모드가 아닐 때는 **요약 정보** 에 식 선언이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d913-108">When not in debug mode, **Quick Info** displays the expression declaration.</span></span> <span data-ttu-id="4d913-109">디버그 모드일 때는 **요약 정보** 에 식 이름과 식의 현재 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d913-109">When in debug mode, **Quick Info** instead displays the name of the expression and its current value.</span></span>  
  
 <span data-ttu-id="4d913-110">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서 IntelliSense에서 지원하는 **구문의 이러한 부분에 대해서만** 요약 정보 [!INCLUDE[tsql](../../includes/tsql-md.md)] 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d913-110">In the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, **Quick Info** is available only for those parts of the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that IntelliSense supports.</span></span> <span data-ttu-id="4d913-111">예를 들어 IntelliSense에서 지원하지 않는 데이터 형식이 있는 개체에 대한 식별자 위로 마우스 포인터를 이동하면 **요약 정보** 팝업 창에 데이터 형식이 지원되지 않는다는 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d913-111">For example, if you move the mouse pointer over the identifier for an object that has a data type that IntelliSense does not support, the **Quick Info** pop-up window contains a message that states that the data type is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d913-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d913-112">See Also</span></span>  
 [<span data-ttu-id="4d913-113">IntelliSense에서 지원되는 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="4d913-113">Transact-SQL Syntax Supported by IntelliSense</span></span>](transact-sql-syntax-supported-by-intellisense.md)  
  
  
