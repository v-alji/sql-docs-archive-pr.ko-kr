---
title: SQLXML이 SQL Server에 설치 되어 있지 않습니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: rothja
ms.author: jroth
ms.openlocfilehash: ffa4cfd8b18dbfd9b4ba05599e2a973ac5f6e888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652700"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a><span data-ttu-id="74a89-102">SQLXML이 SQL Server에 설치되지 않음</span><span class="sxs-lookup"><span data-stu-id="74a89-102">SQLXML Is Not Installed in SQL Server</span></span>
  <span data-ttu-id="74a89-103">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이전에 SQLXML 4.0은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 포함되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제외한 모든 버전의 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 기본 설치에 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-103">Before [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 was released with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and was part of the default installation of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions except for [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="74a89-104">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]부터는 최신 버전의 SQLXML(SQLXML 4.0 SP1)이 더 이상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-104">Starting with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the latest version of SQLXML (SQLXML 4.0 SP1) is no longer included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74a89-105">SQLXML 4.0 s p 1을 사용할 수 있을 때 설치 하려면 [SQLXML Sp1 설치 위치](https://www.microsoft.com/download/details.aspx?id=44272)에서 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-105">To install SQLXML 4.0 SP1 when it is available, download it from [Install Location for SQLXML SP1](https://www.microsoft.com/download/details.aspx?id=44272).</span></span>  
  
 <span data-ttu-id="74a89-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 실행 중인 애플리케이션에 SQLXML 4.0이 필요하고 컴퓨터에 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]가 설치되어 있지 않으면 SQLXML 4.0 SP1을 다운로드하고 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-106">If an application runs on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and requires SQLXML 4.0, and if the computer does not have [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you must download and install SQLXML 4.0 SP1.</span></span>  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a><span data-ttu-id="74a89-107">SQLOLEDB 및 SQL Server Native Client OLE DB 공급자를 사용하는 SQLXML 4.0 SP1의 새로운 데이터 형식 관련 동작</span><span class="sxs-lookup"><span data-stu-id="74a89-107">SQLXML 4.0 SP1 Behavior with New Data Types Using SQLOLEDB and SQL Server Native Client OLE DB Provider</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="74a89-108">에서는 SQLXML을 사용하는 개발자들에게 필요한 다음과 같은 데이터 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-108">introduces the following data types, which developers using SQLXML might want to use:</span></span>  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 <span data-ttu-id="74a89-109">Windows Data Access Components(이전의 Microsoft Data Access Components)에서 제공하는 SQLOLEDB를 통해 SQLXML 4.0 SP1을 사용하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Native Client OLE DB를 통해 SQLXML 4.0 SP1을 사용할 경우 이러한 새로운 형식은 개발자에게 문자열로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-109">When using SQLXML 4.0 SP1 with either SQLOLEDB (from Windows Data Access Components, formerly Microsoft Data Access Components) or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], these new types will appear as strings to a developer.</span></span> <span data-ttu-id="74a89-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0과 함께 SQLXML 4.0 SP1을 사용하는 경우 이러한 네 가지 데이터 형식이 기본 제공 스칼라 형식으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-110">SQLXML 4.0 SP1 will enable these four new data types as built-in scalar types when used with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0.</span></span> <span data-ttu-id="74a89-111">SQLXML 4.0 SP1을 다운로드하기 전에 이러한 형식을 문자열이 아닌 형식에 매핑하면 일부 데이터가 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-111">Until you download SQLXML 4.0 SP1, mapping these types to non-string types might cause truncation of some data.</span></span> <span data-ttu-id="74a89-112">예를 들어 `DateTime2` 로 매핑하면 `xsd:date` 데이터는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` 3.33 밀리초의 전체 자릿수로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="74a89-112">For example, mapping `DateTime2` to `xsd:date` will cause data to be truncated to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` precision of 3.33 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a89-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74a89-113">See Also</span></span>  
 [<span data-ttu-id="74a89-114">SQLXML 4.0 프로그래밍 개념</span><span class="sxs-lookup"><span data-stu-id="74a89-114">SQLXML 4.0 Programming Concepts</span></span>](sqlxml-4-0-programming-concepts.md)  
  
  
