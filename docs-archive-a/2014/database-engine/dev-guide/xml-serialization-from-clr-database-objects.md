---
title: CLR 데이터베이스 개체에서 XML 직렬화 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee93ee4b7bf9cba3f11b329244d4523636cb7704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732975"
---
# <a name="xml-serialization-from-clr-database-objects"></a><span data-ttu-id="54135-102">CLR 데이터베이스 개체에서 XML 직렬화</span><span class="sxs-lookup"><span data-stu-id="54135-102">XML Serialization from CLR Database Objects</span></span>
  <span data-ttu-id="54135-103">XML 직렬화는 다음과 같은 두 가지 시나리오에서 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="54135-103">XML serialization is required for two scenarios:</span></span>  
  
-   <span data-ttu-id="54135-104">CLR(공용 언어 런타임) 개체에서 웹 서비스를 호출하는 경우</span><span class="sxs-lookup"><span data-stu-id="54135-104">Invoking Web Services from common language runtime (CLR) objects.</span></span>  
  
-   <span data-ttu-id="54135-105">UDT(사용자 정의 형식)를 XML로 변환하는 경우</span><span class="sxs-lookup"><span data-stu-id="54135-105">Converting a user-defined type (UDT) to XML.</span></span>  
  
 <span data-ttu-id="54135-106">`XmlSerializer` 클래스를 호출하여 XML 직렬화를 수행하면 일반적으로 추가 직렬화 어셈블리가 생성되어 원본 어셈블리와 함께 프로젝트로 오버로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="54135-106">Performing XML serialization by invoking the `XmlSerializer` class normally generates an additional serialization assembly that is overloaded into the project with the source assembly.</span></span> <span data-ttu-id="54135-107">그러나 CLR에서는 보안을 위해 이 오버로드가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54135-107">However, for security purposes, this overload is disabled in the CLR.</span></span> <span data-ttu-id="54135-108">따라서 내부에서 웹 서비스를 호출 하거나 UDT에서 XML로의 변환을 수행 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 필요한 serialization 어셈블리를 생성 하는 .NET Framework와 함께 제공 되는 **Sgen.exe** 라는 도구를 사용 하 여 어셈블리를 수동으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54135-108">Therefore, to call a web service or perform conversion from UDT to XML inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly must be created manually using a tool called **Sgen.exe** provided with the .NET Framework that generates the necessary serialization assemblies.</span></span> <span data-ttu-id="54135-109">`XmlSerializer`를 호출하는 경우 다음 단계에 따라 직렬화 어셈블리를 직접 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54135-109">When invoking `XmlSerializer`, the serialization assembly must be created manually by following these steps:</span></span>  
  
1.  <span data-ttu-id="54135-110">.NET Framework SDK와 함께 제공 되는 **Sgen.exe** 도구를 실행 하 여 소스 어셈블리에 대 한 XML serializer가 포함 된 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54135-110">Run the **Sgen.exe** tool that is provided with the .NET Framework SDK to create the assembly containing the XML serializers for the source assembly.</span></span>  
  
2.  <span data-ttu-id="54135-111">`CREATE ASSEMBLY` 문을 사용하여 생성한 어셈블리를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="54135-111">Register the generated assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the `CREATE ASSEMBLY` statement.</span></span>  
  
 <span data-ttu-id="54135-112">XML serialization을 수행할 때 나타날 수 있는 오류에 대 한 자세한 내용은 다음 Microsoft 지원 문서 ["동적으로 생성 된 serialization 어셈블리를 로드할 수 없습니다."](https://support.microsoft.com/kb/913668)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54135-112">For information about errors that you may receive when performing XML serialization, see the following Microsoft Support article: ["Cannot load dynamically generated serialization assembly"](https://support.microsoft.com/kb/913668).</span></span>  
  
 <span data-ttu-id="54135-113">XMLSerializer에서 지원하지 않는 데이터 형식에 대한 자세한 내용은 .NET Framework 설명서의 .NET Framework에서 XML 스키마의 바인딩 지원을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="54135-113">For information on data types that are not supported by XMLSerializer, see XML Schema Binding Support in the .NET Framework in the .NET Framework documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54135-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54135-114">See Also</span></span>  
 <span data-ttu-id="54135-115">[CLR 데이터베이스 개체에서 데이터 액세스](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="54135-115">[Data Access from CLR Database Objects](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md) </span></span>  
 [<span data-ttu-id="54135-116">CREATE ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="54135-116">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
