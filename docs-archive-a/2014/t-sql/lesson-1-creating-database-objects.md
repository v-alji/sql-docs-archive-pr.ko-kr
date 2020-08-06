---
title: '1단원: 데이터베이스 개체 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 9fb8656b-0e4e-4ada-b404-4db4d3eea995
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 172fdbcaedc10f9c359befd48ed09ec825aea9bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735764"
---
# <a name="lesson-1-creating-database-objects"></a><span data-ttu-id="3e0c2-102">1단원: 데이터베이스 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="3e0c2-102">Lesson 1: Creating Database Objects</span></span>
  <span data-ttu-id="3e0c2-103">이 단원에서는 데이터베이스를 만들고 데이터베이스에서 테이블을 만든 다음 테이블의 데이터에 액세스 및 변경하는 방법에 대해 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e0c2-103">This lesson shows you how to create a database, create a table in the database, and then access and change the data in the table.</span></span> <span data-ttu-id="3e0c2-104">이 단원은 [!INCLUDE[tsql](../includes/tsql-md.md)]사용을 소개하는 데 목적이 있으므로 이러한 문에 사용 가능한 많은 옵션을 사용하거나 설명하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e0c2-104">Because this lesson is an introduction to using [!INCLUDE[tsql](../includes/tsql-md.md)], it does not use or describe the many options that are available for these statements.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="3e0c2-105">문을 다음과 같은 방법으로 작성하여 [!INCLUDE[ssDE](../includes/ssde-md.md)] 에 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e0c2-105">statements can be written and submitted to the [!INCLUDE[ssDE](../includes/ssde-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="3e0c2-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]사용.</span><span class="sxs-lookup"><span data-stu-id="3e0c2-106">By using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3e0c2-107">이 자습서에서는 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]를 사용한다고 가정하지만 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Microsoft 다운로드 센터 [에서 무료로 다운로드할 수 있는](https://www.microsoft.com/download/details.aspx?id=14630)Express를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e0c2-107">This tutorial assumes that you are using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], but you can also use [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express, which is available as a free download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=14630).</span></span>  
  
-   <span data-ttu-id="3e0c2-108">[sqlcmd 유틸리티](../tools/sqlcmd-utility.md)사용</span><span class="sxs-lookup"><span data-stu-id="3e0c2-108">By using the [sqlcmd utility](../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="3e0c2-109">만드는 애플리케이션에서 연결</span><span class="sxs-lookup"><span data-stu-id="3e0c2-109">By connecting from an application that you create.</span></span>  
  
 <span data-ttu-id="3e0c2-110">코드 문을 전송하는 방법에 상관없이 코드는 동일한 방법과 동일한 사용 권한으로 [!INCLUDE[ssDE](../includes/ssde-md.md)] 에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e0c2-110">The code executes on the [!INCLUDE[ssDE](../includes/ssde-md.md)] in the same way and with the same permissions, regardless of how you submit the code statements.</span></span>  
  
 <span data-ttu-id="3e0c2-111">[!INCLUDE[tsql](../includes/tsql-md.md)] 에서 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]문을 실행하려면 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 를 열고 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3e0c2-111">To run [!INCLUDE[tsql](../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], open [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3e0c2-112">이 단원에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="3e0c2-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="3e0c2-113">데이터베이스 만들기&#40;자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="3e0c2-113">Creating a Database &#40;Tutorial&#41;</span></span>](lesson-1-1-creating-a-database.md)  
  
-   [<span data-ttu-id="3e0c2-114">테이블 만들기&#40;자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="3e0c2-114">Creating a Table &#40;Tutorial&#41;</span></span>](lesson-1-2-creating-a-table.md)  
  
-   [<span data-ttu-id="3e0c2-115">테이블에서 데이터 삽입 및 업데이트&#40;자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="3e0c2-115">Inserting and Updating Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
-   [<span data-ttu-id="3e0c2-116">테이블의 데이터 읽기&#40;자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="3e0c2-116">Reading the Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-4-reading-the-data-in-a-table.md)  
  
-   [<span data-ttu-id="3e0c2-117">요약: 데이터베이스 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="3e0c2-117">Summary: Creating Database Objects</span></span>](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3e0c2-118">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="3e0c2-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3e0c2-119">데이터베이스 만들기&#40;자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="3e0c2-119">Creating a Database &#40;Tutorial&#41;</span></span>](lesson-1-1-creating-a-database.md)  
  
  
