
---
title: "getDatastoreCluster"
title_tag: "vsphere.getDatastoreCluster"
meta_desc: "Documentation for the vsphere.getDatastoreCluster function with examples, input properties, output properties, and supporting types."
---



<!-- WARNING: this file was generated by Pulumi Docs Generator. -->
<!-- Do not edit by hand unless you're certain you know what you are doing! -->

The `vsphere.DatastoreCluster` data source can be used to discover the ID of a
datastore cluster in vSphere. This is useful to fetch the ID of a datastore
cluster that you want to use to assign datastores to using the
`vsphere.NasDatastore` or
`vsphere.VmfsDatastore` resources, or create
virtual machines in using the
`vsphere.VirtualMachine` resource.


{{% examples %}}

## Example Usage

{{< chooser language "typescript,python,go,csharp" / >}}





{{< example csharp >}}

```csharp
using Pulumi;
using VSphere = Pulumi.VSphere;

class MyStack : Stack
{
    public MyStack()
    {
        var datacenter = Output.Create(VSphere.GetDatacenter.InvokeAsync(new VSphere.GetDatacenterArgs
        {
            Name = "dc1",
        }));
        var datastoreCluster = Output.Create(VSphere.GetDatastoreCluster.InvokeAsync(new VSphere.GetDatastoreClusterArgs
        {
            DatacenterId = data.Vsphere_datacenter.Dc.Id,
            Name = "datastore-cluster1",
        }));
    }

}
```


{{< /example >}}


{{< example go >}}

```go
package main

import (
	"github.com/pulumi/pulumi-vsphere/sdk/v3/go/vsphere"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		opt0 := "dc1"
		_, err := vsphere.LookupDatacenter(ctx, &vsphere.LookupDatacenterArgs{
			Name: &opt0,
		}, nil)
		if err != nil {
			return err
		}
		opt1 := data.Vsphere_datacenter.Dc.Id
		_, err = vsphere.LookupDatastoreCluster(ctx, &vsphere.LookupDatastoreClusterArgs{
			DatacenterId: &opt1,
			Name:         "datastore-cluster1",
		}, nil)
		if err != nil {
			return err
		}
		return nil
	})
}
```


{{< /example >}}


{{< example python >}}

```python
import pulumi
import pulumi_vsphere as vsphere

datacenter = vsphere.get_datacenter(name="dc1")
datastore_cluster = vsphere.get_datastore_cluster(datacenter_id=data["vsphere_datacenter"]["dc"]["id"],
    name="datastore-cluster1")
```


{{< /example >}}


{{< example typescript >}}


```typescript
import * as pulumi from "@pulumi/pulumi";
import * as vsphere from "@pulumi/vsphere";

const datacenter = pulumi.output(vsphere.getDatacenter({
    name: "dc1",
}, { async: true }));
const datastoreCluster = vsphere_datacenter_dc.id.apply(id => vsphere.getDatastoreCluster({
    datacenterId: id,
    name: "datastore-cluster1",
}, { async: true }));
```


{{< /example >}}





{{% /examples %}}




## Using getDatastoreCluster {#using}

{{< chooser language "typescript,python,go,csharp" / >}}


{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">function </span>getDatastoreCluster<span class="p">(</span><span class="nx">args</span><span class="p">:</span> <span class="nx">GetDatastoreClusterArgs</span><span class="p">,</span> <span class="nx">opts</span><span class="p">?:</span> <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#InvokeOptions">InvokeOptions</a></span><span class="p">): Promise&lt;<span class="nx"><a href="#result">GetDatastoreClusterResult</a></span>></span></code></pre></div>
{{% /choosable %}}


{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span>get_datastore_cluster(</span><span class="nx">datacenter_id</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
                          <span class="nx">name</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
                          <span class="nx">opts</span><span class="p">:</span> <span class="nx"><a href="/docs/reference/pkg/python/pulumi/#pulumi.InvokeOptions">Optional[InvokeOptions]</a></span> = None<span class="p">) -&gt;</span> GetDatastoreClusterResult</code></pre></div>
{{% /choosable %}}


{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>LookupDatastoreCluster<span class="p">(</span><span class="nx">ctx</span><span class="p"> *</span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#Context">Context</a></span><span class="p">,</span> <span class="nx">args</span><span class="p"> *</span><span class="nx">LookupDatastoreClusterArgs</span><span class="p">,</span> <span class="nx">opts</span><span class="p"> ...</span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#InvokeOption">InvokeOption</a></span><span class="p">) (*<span class="nx"><a href="#result">LookupDatastoreClusterResult</a></span>, error)</span></code></pre></div>

> Note: This function is named `LookupDatastoreCluster` in the Go SDK.

{{% /choosable %}}


{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static class </span><span class="nx">GetDatastoreCluster </span><span class="p">{</span><span class="k">
    public static </span>Task&lt;<span class="nx"><a href="#result">GetDatastoreClusterResult</a></span>> <span class="p">InvokeAsync(</span><span class="nx">GetDatastoreClusterArgs</span><span class="p"> </span><span class="nx">args<span class="p">,</span> <span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.InvokeOptions.html">InvokeOptions</a></span><span class="p">? </span><span class="nx">opts = null<span class="p">)</span><span class="p">
}</span></code></pre></div>
{{% /choosable %}}



The following arguments are supported:


{{% choosable language csharp %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="name_csharp">
<a href="#name_csharp" style="color: inherit; text-decoration: inherit;">Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name or absolute path to the datastore cluster.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="datacenterid_csharp">
<a href="#datacenterid_csharp" style="color: inherit; text-decoration: inherit;">Datacenter<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The managed object reference
ID of the datacenter the datastore cluster is located in.
This can be omitted if the search path used in `name` is an absolute path.
For default datacenters, use the id attribute from an empty
`vsphere.Datacenter` data source.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language go %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="name_go">
<a href="#name_go" style="color: inherit; text-decoration: inherit;">Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name or absolute path to the datastore cluster.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="datacenterid_go">
<a href="#datacenterid_go" style="color: inherit; text-decoration: inherit;">Datacenter<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The managed object reference
ID of the datacenter the datastore cluster is located in.
This can be omitted if the search path used in `name` is an absolute path.
For default datacenters, use the id attribute from an empty
`vsphere.Datacenter` data source.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language nodejs %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="name_nodejs">
<a href="#name_nodejs" style="color: inherit; text-decoration: inherit;">name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name or absolute path to the datastore cluster.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="datacenterid_nodejs">
<a href="#datacenterid_nodejs" style="color: inherit; text-decoration: inherit;">datacenter<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The managed object reference
ID of the datacenter the datastore cluster is located in.
This can be omitted if the search path used in `name` is an absolute path.
For default datacenters, use the id attribute from an empty
`vsphere.Datacenter` data source.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="name_python">
<a href="#name_python" style="color: inherit; text-decoration: inherit;">name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name or absolute path to the datastore cluster.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="datacenter_id_python">
<a href="#datacenter_id_python" style="color: inherit; text-decoration: inherit;">datacenter_<wbr>id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The managed object reference
ID of the datacenter the datastore cluster is located in.
This can be omitted if the search path used in `name` is an absolute path.
For default datacenters, use the id attribute from an empty
`vsphere.Datacenter` data source.
{{% /md %}}</dd></dl>
{{% /choosable %}}




## getDatastoreCluster Result {#result}

The following output properties are available:



{{% choosable language csharp %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="id_csharp">
<a href="#id_csharp" style="color: inherit; text-decoration: inherit;">Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.
{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="name_csharp">
<a href="#name_csharp" style="color: inherit; text-decoration: inherit;">Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="datacenterid_csharp">
<a href="#datacenterid_csharp" style="color: inherit; text-decoration: inherit;">Datacenter<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language go %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="id_go">
<a href="#id_go" style="color: inherit; text-decoration: inherit;">Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.
{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="name_go">
<a href="#name_go" style="color: inherit; text-decoration: inherit;">Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="datacenterid_go">
<a href="#datacenterid_go" style="color: inherit; text-decoration: inherit;">Datacenter<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language nodejs %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="id_nodejs">
<a href="#id_nodejs" style="color: inherit; text-decoration: inherit;">id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.
{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="name_nodejs">
<a href="#name_nodejs" style="color: inherit; text-decoration: inherit;">name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="datacenterid_nodejs">
<a href="#datacenterid_nodejs" style="color: inherit; text-decoration: inherit;">datacenter<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="id_python">
<a href="#id_python" style="color: inherit; text-decoration: inherit;">id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.
{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="name_python">
<a href="#name_python" style="color: inherit; text-decoration: inherit;">name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="datacenter_id_python">
<a href="#datacenter_id_python" style="color: inherit; text-decoration: inherit;">datacenter_<wbr>id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}





<h2 id="package-details">Package Details</h2>
<dl class="package-details">
	<dt>Repository</dt>
	<dd><a href="https://github.com/pulumi/pulumi-vsphere">https://github.com/pulumi/pulumi-vsphere</a></dd>
	<dt>License</dt>
	<dd>Apache-2.0</dd>
	<dt>Notes</dt>
	<dd>{{% md %}}This Pulumi package is based on the [`vsphere` Terraform Provider](https://github.com/hashicorp/terraform-provider-vsphere).{{% /md %}}</dd>
</dl>

