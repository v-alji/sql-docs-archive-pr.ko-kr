---
title: 작업 수행(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.performingoperation.f1
ms.assetid: 83259509-71d6-4a64-a7f2-4e9603b30bd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6cdac605da2288149909a3fb6e9f245e10eebf8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652931"
---
# <a name="performing-operation-sql-server-import-and-export-wizard"></a><span data-ttu-id="f5c7a-102">작업을 수행하는 중(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="f5c7a-102">Performing Operation (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="f5c7a-103">**작업을 수행하는 중** 페이지를 사용하여 가져오기/내보내기 작업의 진행률 및 결과를 보고 필요한 경우 작업을 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-103">Use the **Performing Operation** page to view the progress and the results of the import/export operation, and to interrupt the operation if necessary.</span></span>  
  
 <span data-ttu-id="f5c7a-104">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="f5c7a-105">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 사용 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="f5c7a-106">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="f5c7a-107">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="f5c7a-108">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="f5c7a-109">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f5c7a-110">옵션</span><span class="sxs-lookup"><span data-stu-id="f5c7a-110">Options</span></span>  
 <span data-ttu-id="f5c7a-111">**동작**</span><span class="sxs-lookup"><span data-stu-id="f5c7a-111">**Action**</span></span>  
 <span data-ttu-id="f5c7a-112">동작의 일부인 각 작업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-112">Displays each action that is part of the operation.</span></span>  
  
 <span data-ttu-id="f5c7a-113">**상태**</span><span class="sxs-lookup"><span data-stu-id="f5c7a-113">**Status**</span></span>  
 <span data-ttu-id="f5c7a-114">각 동작의 성공 또는 실패 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-114">Displays the success or failure of each action.</span></span>  
  
 <span data-ttu-id="f5c7a-115">**Message**</span><span class="sxs-lookup"><span data-stu-id="f5c7a-115">**Message**</span></span>  
 <span data-ttu-id="f5c7a-116">동작에서 생성하는 정보 및 오류 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-116">Displays informational and error messages that the action might generate.</span></span>  
  
 <span data-ttu-id="f5c7a-117">**Filter**</span><span class="sxs-lookup"><span data-stu-id="f5c7a-117">**Filter**</span></span>  
 <span data-ttu-id="f5c7a-118">오류 또는 경고만 표시할 것인지, 아니면 성공한 동작만 표시할 것인지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-118">Choose whether you want to display only errors, warnings, or successful actions.</span></span> <span data-ttu-id="f5c7a-119">**모든 동작 표시**를 선택하여 기본 표시로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-119">You can revert to the default display by choosing **Show All Actions**.</span></span>  
  
 <span data-ttu-id="f5c7a-120">**중지**</span><span class="sxs-lookup"><span data-stu-id="f5c7a-120">**Stop**</span></span>  
 <span data-ttu-id="f5c7a-121">필요한 경우 **중지** 단추를 사용하여 작업을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-121">Interrupt the operation, if necessary, by using the **Stop** button.</span></span>  
  
 <span data-ttu-id="f5c7a-122">**Report**</span><span class="sxs-lookup"><span data-stu-id="f5c7a-122">**Report**</span></span>  
 <span data-ttu-id="f5c7a-123">결과 보고서를 보거나, 보고서를 파일에 저장하거나, 보고서를 클립보드에 복사하거나, 보고서를 전자 메일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f5c7a-123">View a report of the results, save the report to a file, copy the report to the clipboard, or send the report by e-mail.</span></span>  
  
  
