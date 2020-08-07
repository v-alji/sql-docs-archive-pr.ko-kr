---
title: SQL Server에서 사용자 정의 형식 사용 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- user-defined types [CLR integration], queries
- UDTs [CLR integration], queries
- user-defined types [CLR integration], Transact-SQL
- UDTs [CLR integration], Transact-SQL
- queries [CLR integration]
ms.assetid: 807376fb-1f1a-4f2a-8cf8-a622c5858634
author: rothja
ms.author: jroth
ms.openlocfilehash: c9fed9ad4e73102eadd1374ff87d2a46d0ff4126
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730752"
---
# <a name="working-with-user-defined-types-in-sql-server"></a><span data-ttu-id="05126-102">SQL 서버의 사용자 정의 형식 작업</span><span class="sxs-lookup"><span data-stu-id="05126-102">Working with User-Defined Types in SQL Server</span></span>
  <span data-ttu-id="05126-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 일반 쿼리 구문을 사용 하 여 언어에서의 UDT (사용자 정의 형식) 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05126-103">You can access user-defined type (UDT) functionality in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[tsql](../../includes/tsql-md.md)] language by using regular query syntax.</span></span> <span data-ttu-id="05126-104">UDT는 데이터베이스 개체 정의에 사용하거나 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리, 함수 및 저장 프로시저의 변수, 그리고 함수 및 저장 프로시저의 인수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05126-104">UDTs can be used in the definition of database objects, as variables in [!INCLUDE[tsql](../../includes/tsql-md.md)] batches, in functions and stored procedures, and as arguments in functions and stored procedures.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05126-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="05126-105">In This Section</span></span>  
 [<span data-ttu-id="05126-106">UDT 테이블 및 열 정의</span><span class="sxs-lookup"><span data-stu-id="05126-106">Defining UDT Tables and Columns</span></span>](working-with-user-defined-types-defining-udt-tables-and-columns.md)  
 <span data-ttu-id="05126-107">[!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 테이블에 UDT 열을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05126-107">Describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to create a UDT column in a table.</span></span>  
  
 [<span data-ttu-id="05126-108">UDT 데이터 조작</span><span class="sxs-lookup"><span data-stu-id="05126-108">Manipulating UDT Data</span></span>](working-with-user-defined-types-manipulating-udt-data.md)  
 <span data-ttu-id="05126-109">[!INCLUDE[tsql](../../includes/tsql-md.md)]에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]을 사용하여 UDT 데이터로 작업하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05126-109">Describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to work with UDT data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05126-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05126-110">See Also</span></span>  
 [<span data-ttu-id="05126-111">CLR 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="05126-111">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
