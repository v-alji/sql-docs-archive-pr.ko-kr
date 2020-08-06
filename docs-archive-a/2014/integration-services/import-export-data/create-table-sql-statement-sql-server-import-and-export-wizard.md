---
title: 테이블 생성 SQL 문(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3fc2054711708a27691f2d7219c33749f11b977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652935"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a><span data-ttu-id="c4e2c-102">테이블 생성 SQL 문(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="c4e2c-102">Create Table SQL Statement (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="c4e2c-103">**테이블 생성 SQL 문** 대화 상자를 사용 하 여 자동으로 생성 된 문을 보거나 목적에 맞게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-103">Use the **Create Table SQL Statement** dialog box to view the statement that was generated automatically, or to modify it for your purposes.</span></span> <span data-ttu-id="c4e2c-104">이 문을 수정하면 관련 변경 내용을 열 매핑에 적용해야 할 수도 있고 그에 따라 편집된 SQL 문을 직접 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-104">If you modify this statement, you may also have to make associated changes to column mapping, and you will have to maintain the edited SQL statement manually thereafter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="c4e2c-105">는 연결된 데이터 원본에 따라 기본 CREATE TABLE 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-105">generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="c4e2c-106">원본 테이블에 선언된 FILESTREAM 특성이 포함된 열이 있어도 기본 CREATE TABLE 문은 FILESTREAM 특성을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-106">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="c4e2c-107">FILESTREAM 특성이 포함된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소를 실행하려면 먼저 대상 데이터베이스에서 FILESTREAM 스토리지를 구현하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-107">To run an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="c4e2c-108">그런 다음 **테이블 만들기** 대화 상자에서 FILESTREAM 특성을 CREATE TABLE 문에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-108">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="c4e2c-109">자세한 내용은 [Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-109">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="c4e2c-110">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-110">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="c4e2c-111">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 사용 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-111">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="c4e2c-112">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-112">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="c4e2c-113">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-113">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="c4e2c-114">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-114">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="c4e2c-115">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-115">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c4e2c-116">옵션</span><span class="sxs-lookup"><span data-stu-id="c4e2c-116">Options</span></span>  
 <span data-ttu-id="c4e2c-117">**SQL 문**</span><span class="sxs-lookup"><span data-stu-id="c4e2c-117">**SQL statement**</span></span>  
 <span data-ttu-id="c4e2c-118">자동으로 생성된 SQL 문을 표시하고 편집할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-118">Displays the auto-generated SQL statement and lets it be edited.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4e2c-119">SQL 문에 캐리지 리턴을 포함하려면 Ctrl+Enter를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-119">If you want to include a carriage return in the SQL statement, press CTRL+ENTER.</span></span> <span data-ttu-id="c4e2c-120">Enter 키만 누르면 대화 상자가 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-120">If you press only ENTER, the dialog box closes.</span></span>  
  
 <span data-ttu-id="c4e2c-121">**자동**</span><span class="sxs-lookup"><span data-stu-id="c4e2c-121">**Autogenerate**</span></span>  
 <span data-ttu-id="c4e2c-122">기본 SQL 문을 수정한 경우 **자동 생성**을 클릭하여 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e2c-122">Restore the default SQL statement, if you have modified it, by clicking **Autogenerate**.</span></span>  
  
  
