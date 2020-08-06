---
title: 열 변환 정보 대화 상자(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9207e76191060c56acad37db734827579a83aae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652941"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a><span data-ttu-id="f16d6-102">열 변환 정보 대화 상자(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="f16d6-102">Column Conversion Details Dialog Box (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="f16d6-103">**열 변환 정보** 대화 상자를 사용 하 여 개별 열에 대 한 자세한 변환 정보를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-103">Use the **Column Conversion Details** dialog box to review detailed conversion information about an individual column.</span></span> <span data-ttu-id="f16d6-104">이 변환 정보에는 원본 및 대상의 열 데이터 형식과 마법사에서 수행할 변환이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-104">This conversion information contains the column's data type at the source and the destination, and the conversion that the wizard will perform.</span></span> <span data-ttu-id="f16d6-105">또한 이 페이지에는 필요한 데이터 형식 변환을 결정하기 위해 마법사에서 사용하는 데이터 형식 매핑 파일이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-105">This page also lists the data type mapping files that the wizard uses to determine the data type conversions that are required.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="f16d6-106">가 설치되는 동안 이러한 데이터 형식 매핑 파일이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-106">installs these data type mapping files during setup.</span></span>  
  
 <span data-ttu-id="f16d6-107">**열 변환 정보 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="f16d6-107">**To open the Column Conversion Details dialog box**</span></span>  
  
1.  <span data-ttu-id="f16d6-108">가져오기 및 내보내기 마법사의 **데이터 형식 문제 검토** 페이지에 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **테이블** 목록에서 테이블을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-108">On the **Review Data Type Issues** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, in the **Table** list, select a table.</span></span>  
  
2.  <span data-ttu-id="f16d6-109">**데이터 형식 매핑** 목록에서 변환 세부 정보를 보려는 열이 포함 된 행을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-109">In the **Data type mapping** list, double-click the row that contains the column for which you want to view conversion details.</span></span>  
  
 <span data-ttu-id="f16d6-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가져오기 및 내보내기 마법사에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f16d6-110">To learn more about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="f16d6-111">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f16d6-111">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="f16d6-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 원본에서 대상으로 데이터를 복사할 목적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-112">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="f16d6-113">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-113">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="f16d6-114">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f16d6-114">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="f16d6-115">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f16d6-115">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
  
