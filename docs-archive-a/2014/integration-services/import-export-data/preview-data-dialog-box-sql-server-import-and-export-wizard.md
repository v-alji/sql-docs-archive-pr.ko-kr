---
title: 데이터 미리 보기 대화 상자(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.previewdata.f1
ms.assetid: 423ac26a-ba02-4fdf-88b4-07995fe4a97e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 17debc001d8ba7826fe845c006e944e5a3dc87a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652924"
---
# <a name="preview-data-dialog-box-sql-server-import-and-export-wizard"></a><span data-ttu-id="f4df2-102">데이터 미리 보기 대화 상자(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="f4df2-102">Preview Data Dialog Box (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="f4df2-103">**데이터 미리 보기** 대화 상자를 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사가 데이터 원본에 보내는 쿼리를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4df2-103">Use the **Preview Data** dialog box to see the query that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard will send to the data source.</span></span> <span data-ttu-id="f4df2-104">또한 이 대화 상자를 사용하여 최대 200개의 샘플 데이터 행을 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4df2-104">You can also use this dialog box to preview up to 200 rows of sample data.</span></span>  
  
 <span data-ttu-id="f4df2-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가져오기 및 내보내기 마법사에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f4df2-105">To learn more about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="f4df2-106">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f4df2-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="f4df2-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 원본에서 대상으로 데이터를 복사할 목적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4df2-107">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="f4df2-108">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4df2-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="f4df2-109">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4df2-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="f4df2-110">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4df2-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
 <span data-ttu-id="f4df2-111">**데이터 미리 보기 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="f4df2-111">**To open the Preview Data dialog box**</span></span>  
  
-   <span data-ttu-id="f4df2-112">가져오기 및 내보내기 마법사의 **원본 테이블 및 뷰 선택** 페이지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **미리 보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4df2-112">On the **Select Source Tables and Views** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, click **Preview**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f4df2-113">옵션</span><span class="sxs-lookup"><span data-stu-id="f4df2-113">Options</span></span>  
 <span data-ttu-id="f4df2-114">**원본**</span><span class="sxs-lookup"><span data-stu-id="f4df2-114">**Source**</span></span>  
 <span data-ttu-id="f4df2-115">마법사가 데이터 원본에 보내는 쿼리를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4df2-115">Displays the query that the wizard will send to the data source.</span></span>  
  
 <span data-ttu-id="f4df2-116">**샘플 데이터 표**</span><span class="sxs-lookup"><span data-stu-id="f4df2-116">**Sample data grid**</span></span>  
 <span data-ttu-id="f4df2-117">쿼리에서 반환되는 샘플 데이터 행을 최대 200개까지 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4df2-117">Displays up to 200 rows of sample data that the query returned.</span></span>  
  
  
